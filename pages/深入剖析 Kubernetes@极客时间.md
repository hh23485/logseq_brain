tags:: 极客时间，Kubernetes，笔记
src:: [深入剖析 Kubernetes (geekbang.org)](https://time.geekbang.org/column/intro/100015201?utm_campaign=iTab&utm_content=iTab&utm_medium=iTab&utm_source=iTab&utm_term=iTab&tab=catalog)

- 容器技术概念入门
	- 略
- Kubernetes
	- 为什么我们需要 pod
	  collapsed:: true
		- 进程并非独立运行，而是需要组合一起完成工作，因此会存在进程组的需求，让三个进程同时存在于一台机器上
		- 容器的单进程模式会导致这三个应用不得不被分配在三个独立的容器中
		- Swarm 并没有能够处理好成组调度的功能
		- Google 提出了 Pod，是 Kubernetes 的调度的最小单位，所有的资源都是按照 pod 的需求进行计算，能够自然而然的提供成组调度能力
	- Pod 的实现原理
	  collapsed:: true
		- Pod 只是一个逻辑概念，在物理上并不存在一个叫做 pod 的实际隔离边界
		- Pod 中的容器共享了同一个 network namespace，可以共享 Volume
			- 但是这和普通的共享 namespace 的方式并不相同，如果直接使用 `$ docker run --net=B --volumes-from=B --name=A image-A ...` 会导致成组的容器之间形成了拓扑关系，被依赖的容器总是优先启动
			- Kubernetes 会创建一个中间容器，叫做 infra 容器，在容器中创建 namespace，然后其他的容器都依赖该 infra 容器
			  ![](https://static001.geekbang.org/resource/image/8c/cf/8c016391b4b17923f38547c498e434cf.png?wh=490*665)
				- infra 容器中是一个固定的非常轻量的镜像叫做 k8s.gcr.io/pause，使用汇编语言编写，用于出于暂停状态的容器
			- Pod 生命周期与 infra 容器一致
			- 因此可以在 Pod level 定义 volume 等信息，交给 infra 来完成，而不用考虑容器级别，一定绑定，就会同时挂载到 pod 的所有容器中
	- 容器设计模式
	  collapsed:: true
		- 在容器中跑多个进程的时候，首先就需要考虑是否应该被描述为一个 Pod 中的多个容器
		- 多个容器可以很好的解耦本身并不完全相干但需要协作的多个进程
			- 对于 tomcat 和 war 包而言，每次都打在一块，以至于 tomcat 和 war 包更新的时候都不得不重新更新镜像。而拆开 tomcat 和 war 为两个镜像时，就可以独立发布升级，互相不干涉
			- 由于共享了 network 和 volume，sidecar 中可以放入日志收集、网络处理等治理逻辑，而不需要侵入应用本身和应用镜像。istio 就是这方面著名的开源项目。
	- Pod 对象解析
	  src:: [14 | 深入解析Pod对象（一）：基本概念 (geekbang.org)](https://time.geekbang.org/column/article/40366?utm_campaign=iTab&utm_content=iTab&utm_medium=iTab&utm_source=iTab&utm_term=iTab), [15 | 深入解析Pod对象（二）：使用进阶 (geekbang.org)](https://time.geekbang.org/column/article/40466?utm_campaign=iTab&utm_content=iTab&utm_medium=iTab&utm_source=iTab&utm_term=iTab)
		- 重要字段
			- NodeSelector：用于设置 pod 可以被调度到携带哪些标签的节点上
			- NodeName：一旦设置调度器就认为该 Pod 已经被调度了
			- HostAliases：用于设置 Pod 例的 hosts 文件内容
				- ``` yaml
				  apiVersion: v1
				  kind: Pod
				  ...
				  spec:
				    hostAliases:
				    - ip: "10.1.2.3"
				      hostnames:
				      - "foo.remote"
				      - "bar.remote"
				  ...
				  
				  会生成如下 hosts
				  
				  cat /etc/hosts
				  # Kubernetes-managed hosts file.
				  127.0.0.1 localhost
				  ...
				  10.244.135.10 hostaliases-pod
				  10.1.2.3 foo.remote
				  10.1.2.3 bar.remote
				  ```
			- shareProcessNamespace：设置容器是否共享 PID Namespace
				- 同理凡是 namespace 的设置，都是在 POD level 完成
					- hostNamework，hostIPC, hostPID 也都是在 pod 的 spec 中设置
			- Containers 字段
				- ImagePullPolicy：设置是否拉取镜像
				- Lifecycle：用于在容器状态发生变化时触发一系列钩子
					- ``` yaml
					  apiVersion: v1
					  kind: Pod
					  metadata:
					    name: lifecycle-demo
					  spec:
					    containers:
					    - name: lifecycle-demo-container
					      image: nginx
					      lifecycle:
					        postStart:
					          exec:
					            command: ["/bin/sh", "-c", "echo Hello from the postStart handler > /usr/share/message"]
					        preStop:
					          exec:
					            command: ["/usr/sbin/nginx","-s","quit"]
					  ```
					- #+BEGIN_NOTE
					  postStart 执行的时候，是 EntryPoint 执行之后，不过这时候 Entrypoint 可能还没有执行结束
					  #+END_NOTE
					- #+BEGIN_NOTE
					  如果 postStart 执行失败，Pod 也会启动失败
					  #+END_NOTE
			- Status
				- 除了 Metadata 和 Spec 之外的第三个重要的字段
				- pod.status.phase 就是 pod 当前的状态
					- Pending
					- Running
					- Succeeded
					- Failed
					- Unknown
				- 在状态下还有一组 Conditions 用来标识细分状态，描述当前 status 的原因
					- PodScheduled
					- Ready：表示当前已经启动完成，并且已经能够对外提供服务
					- Initialized
					- Unschedulable
		- Pod 的定义在 `$GOPATH/src/k8s.io/kubernetes/vendor/k8s.io/api/core/v1/types.go` 中，可以阅读
		- Volume
			- 可投影的 Volume 有 4 种
				- Secret
					- 可参考如下
						- ``` yml
						  apiVersion: v1
						  kind: Pod
						  metadata:
						    name: test-projected-volume 
						  spec:
						    containers:
						    - name: test-secret-volume
						      image: busybox
						      args:
						      - sleep
						      - "86400"
						      volumeMounts:
						      - name: mysql-cred
						        mountPath: "/projected-volume"
						        readOnly: true
						    volumes:
						    - name: mysql-cred
						      projected:
						        sources:
						        - secret:
						            name: user
						        - secret:
						            name: pass
						  ```
					- 这些 secret 需要提前使用 `kubectl create secret` 来创建
						- ``` bash
						  $ cat ./username.txt
						  admin
						  $ cat ./password.txt
						  c1oudc0w!
						  
						  $ kubectl create secret generic user --from-file=./username.txt
						  $ kubectl create secret generic pass --from-file=./password.txt
						  
						  ```
					- 当然使用 yaml 也可以创建
						- ``` yml
						  apiVersion: v1
						  kind: Secret
						  metadata:
						    name: mysecret
						  type: Opaque
						  data:
						    user: YWRtaW4=
						    pass: MWYyZDFlMmU2N2Rm
						  
						  ```
					- 特别的是，这些字段如果被修改，容器里也会被更新（定时），而不是一次性初始化时灌入的数据
					- 不过生产环境中需要加密之后才能放入，这里只是当做明文存入了集群的 etcd
				- ConfigMap
					- 与 secret 类似
						- properties:
							- ``` ini
							  # .properties文件的内容
							  $ cat example/ui.properties
							  color.good=purple
							  color.bad=yellow
							  allow.textmode=true
							  how.nice.to.look=fairlyNice
							  ```
						- 创建 config Map
							- ``` bash
							  # 从.properties文件创建ConfigMap
							  $ kubectl create configmap ui-config --from-file=example/ui.properties
							  
							  ```
						- 查看
							- ``` yml
							  # 查看这个ConfigMap里保存的信息(data)
							  $ kubectl get configmaps ui-config -o yaml
							  apiVersion: v1
							  data:
							    ui.properties: |
							      color.good=purple
							      color.bad=yellow
							      allow.textmode=true
							      how.nice.to.look=fairlyNice
							  kind: ConfigMap
							  metadata:
							    name: ui-config
							    ...
							  
							  ```
				- Downward API
					- 用于获取 pod 对象本身的信息
					- ``` yml
					  apiVersion: v1
					  kind: Pod
					  metadata:
					    name: test-downwardapi-volume
					    labels:
					      zone: us-est-coast
					      cluster: test-cluster1
					      rack: rack-22
					  spec:
					    containers:
					      - name: client-container
					        image: k8s.gcr.io/busybox
					        command: ["sh", "-c"]
					        args:
					        - while true; do
					            if [[ -e /etc/podinfo/labels ]]; then
					              echo -en '\n\n'; cat /etc/podinfo/labels; fi;
					            sleep 5;
					          done;
					        volumeMounts:
					          - name: podinfo
					            mountPath: /etc/podinfo
					            readOnly: false
					    volumes:
					      - name: podinfo
					        projected:
					          sources:
					          - downwardAPI:
					              items:
					                - path: "labels"
					                  fieldRef:
					                    fieldPath: metadata.labels
					  
					  ```
						- 这里将 metadata.labels 作为 labels 路径
						- 然后将路径挂载到 /etc/podinfo 下
						- 可以在容器中访问 /etc/podinfo/labels 来获取
				- ServiceAccountToken
					-
		-