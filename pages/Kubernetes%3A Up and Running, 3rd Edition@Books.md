tags:: [[Kubernetes]], [[读书笔记]]

- 第二章 容器基础
	- “Docker镜像格式”和“容器镜像”这两个短语可能有点令人困惑。镜像不是单个文件，而是指向其他文件的清单文件的规范。用户通常将清单和相关文件视为一个单元。
		- Docker 在此基础上提供了构建、上传和下载的 API
- 第三章 部署 Kubernetes
	- `minikube start --`，启动之前保证 docker 不在 root 权限下运行，且已经安装 kubectl
	- `kubectl get componentstatuses` 启动之后可以得到如下组件
		- ``` 
		  kubectl get componentstatuses
		  Warning: v1 ComponentStatus is deprecated in v1.19+
		  NAME                 STATUS    MESSAGE   ERROR
		  scheduler            Healthy   ok
		  controller-manager   Healthy   ok
		  etcd-0               Healthy   ok
		  ```
		- `controller-manager` 负责运行各种控制器，以调节集群中的行为；例如，确保服务的所有副本都可用且健康。
		- `scheduler` 负责将不同的 Pod 放置在集群中的不同节点上。
		- 最后， `etcd` 服务器是集群的存储，存储着所有的 API 对象。
	-