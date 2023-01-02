file:: [The_Serverless_Computing_Survey_A_Technical_Primer_for_Design_Architecture_1670129409560_0.pdf](../assets/The_Serverless_Computing_Survey_A_Technical_Primer_for_Design_Architecture_1670129409560_0.pdf)
file-path:: ../assets/The_Serverless_Computing_Survey_A_Technical_Primer_for_Design_Architecture_1670129409560_0.pdf

- promising architecture for deploying microservices, serverless computing has recently attracted more and more attention in both industry and academia
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c2879-c61c-4d1d-90e0-de52d9031cf4
- Due to its inherent scalability and flexibility, serverless computing becomes attractive and more pervasive for ever-growing Internet services
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c2882-bd29-447a-9bc8-4e0ed38b6dc4
- he existing challenges and compromises still wait for more advanced research and solutions to further explore the potentials of the serverless computing mode
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c28a1-c9fc-4df4-9536-399280a124eb
- surveys and elaborates the research domains in the serverless context by decoupling the architecture into four stack layers: Virtualization, Encapsule, System Orchestration, and System Coordination
  ls-type:: annotation
  hl-page:: 1
  hl-color:: green
  id:: 638c28c6-35ad-4828-a907-1f8fe7a9cfd5
- Definition of Serverless Computing
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c2951-7cef-456b-ac28-2a5be85820a9
- Traditional Infrastructure-as-a-Service ([[IaaS]]) deployment mode demands a long-term running server for sustainable service delivery
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c2a2b-b430-4989-abbe-aaca559d4ae3
- exclusive allocation needs to retain resources regardless of whether the user application is running or not.
  ls-type:: annotation
  hl-page:: 1
  hl-color:: red
  id:: 638c2a40-eb22-4da3-926b-5e1af65859c5
- results in low resource utilization in current data centers by only about 10% on average, especially for an online service with a diurnal pattern.
  ls-type:: annotation
  hl-page:: 1
  hl-color:: red
  id:: 638c2a4f-0910-4b4b-ab2d-0972be6f2d12
- attracts the development of a platform-managed on-demand
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c2af0-1d21-4a4f-8288-19121e121cba
- higher resource utilization
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 638c2b0c-9963-4d6c-bae9-10c5d94fb85c
  hl-stamp:: 1670130449918
- lower cloud computing costs.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 638c2b1b-378d-4c1b-9bf7-5c1fce695a7f
- To this end, [[serverless]] computing was put forward,
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c2b70-2ef8-47eb-8d1c-29759c526155
  hl-stamp:: 1670130546414
- [65]
  ls-type:: annotation
  hl-page:: 31
  hl-color:: yellow
  id:: 638c2bf4-fe5e-494e-a6db-39f4f9d8a54d
- Berkeley View [65]
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c2c5b-d23f-4947-8f73-60504e99a251
- 𝑆𝑒𝑟𝑣𝑒𝑟𝑙𝑒𝑠𝑠 𝐶𝑜𝑚𝑝𝑢𝑡𝑖𝑛𝑔 = 𝐹𝑎𝑎𝑆 (𝐹𝑢𝑛𝑐𝑡𝑖𝑜𝑛-𝑎𝑠-𝑎-𝑆𝑒𝑟𝑣𝑖𝑐𝑒) + 𝐵𝑎𝑎𝑆 (𝐵𝑎𝑐𝑘𝑒𝑛𝑑-𝑎𝑠-𝑎-𝑆𝑒𝑟𝑣𝑖𝑐𝑒).
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c2cbf-a800-44c1-9921-b2e3213a1deb
- ‘Serverless’ is interchangeable with ‘FaaS’
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c2ce9-06fe-4ff5-9d3f-297a8bdd4412
- 𝐹𝑎𝑎𝑆 model enables the function isolation and invocation
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 638c2d00-17f6-4bc2-a726-5169857097e6
- 𝐵𝑎𝑎𝑆 provides overall backend support for online services.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 638c2d05-2ac3-45d6-8be9-dd180edd3299
- [[𝐹𝑎𝑎𝑆]] model, an application is sliced into **functions** or **functionlevel microservices** [ 26, 45 , 57, 65, 117, 141 ]
  hl-page:: 2
  ls-type:: annotation
  id:: 638c2d69-8b82-4ecb-a639-38df62914be2
  hl-color:: blue
  hl-stamp:: 1670131115477
- 𝐵𝑎𝑎𝑆 covers a wide range of services that any application relies on can be categorized into it.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 638c2da0-d898-4203-ab2b-4c805b07c381
  hl-stamp:: 1670131117988
- [:span]
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c2f99-bd82-45a6-bca4-dd60f740d073
  hl-type:: area
  hl-stamp:: 1670131607894
- receives triggered API queries from the users, validates them, and invokes the functions 
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c3007-8f76-4289-ba29-901ec44b8015
- by creating new sandboxes (aka the cold startup [15, 28 , 65])
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c3017-dd38-4963-b60e-5ea3701a13e5
- reusing running warm ones (aka the warm startup).
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c301e-7c08-4a3e-b1f6-b0a5618d0c42
- ==isolation== ensures that each function invocation runs in an individual container or a virtual machine assigned from an access-control controller.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c303a-ecf0-465a-ae17-25ecfe7ba5a4
  hl-stamp:: 1670131775153
- he serverless system can be triggered to provide on-demand isolated instances and ==scale== them horizontally according to the actual application workload.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c3097-abb9-4f42-9c41-1f335e142faa
- Each execution worker accesses a backend database to save execution results [23]
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c30dd-b6f1-4fa4-8748-17427486279b
- further configuring triggers and bridging interactions, users can customize the execution for complex applications
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c30f7-f20a-4d13-8178-e21507095ab4
- Auto-scaling
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c33b0-dd96-484e-9580-5431b88ad4a8
- Flexible scheduling
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c33b8-b95f-4439-9a33-ebf4369c9e0a
- Event-driven.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c33be-7271-49e9-a464-e82bd690f7e8
- Transparent development
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c33c4-8870-4187-baf1-bd101d7e9ac8
- ==Pay-as-you-go==.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c33cb-5c6c-4a90-870c-931ace8d1357
- The indispensable factor in identifying a serverless system is performing horizontal and vertical scaling when accommodating workload dynamics
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 638c3434-36c2-49f4-9ca1-3985389f8a11
  hl-stamp:: 1670132799806
- **no longer bound to a specific server**
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 638c3466-3ecc-49d4-a369-1e338fa9354c
  hl-stamp:: 1670132846514
- serverless controller dynamically schedules applications 
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 638c4e2c-c2f1-420f-ba9e-7e7e10da0eec
- according to the resource usage in the cluster, while ensuring load balancing and performance assurances
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c4e51-b62a-4093-9b0b-a4a1d210adf4
  hl-stamp:: 1670139474954
- also takes the multi-region collaboration into account [ 154 ].
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c4e67-2930-4eb6-9f72-829fa536483c
- allows the workload queries to be distributed across a broader range of regions [119 ].
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c4e7d-410e-4f48-9280-0bd306700195
- The development of cloud infrastructures inspires the emergence of cloud-native computing. 
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 638c283c-b8e5-4f9a-8995-f4be5ea35a67
- triggered by events
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c76d0-ff03-4612-8b39-48f3c33bd64a
- arrival of RESTful HTTP queries, the update of a message queue, or new data to a storage service
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c76dd-39c9-485e-91da-a42d337c97ac
- binding events to functions with triggers and rules
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c7717-9008-4bbd-852f-cebe7472d3f3
- makes relationships between events and the system detectable, enabling different collaboration responses to different events
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c7732-ed4a-4cad-937c-45affd683ec3
- ==Cloud-Native Computing Foundation (CNCF) serverless group also published [[CloudEvents]] specifications for commonly describing event metadata to provide interoperability.==
  hl-page:: 3
  ls-type:: annotation
  id:: 638c7764-a45d-4602-a7ce-ec2c8fe7a41c
  hl-color:: blue
- cloud vendors should ensure available physical nodes, isolated sandboxes, software runtimes, and computing power while making them transparent to maintainers.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c77ed-47a9-4d17-ba79-49538b081f10
- should also integrate DevOps tools to help deploy and iterate more efficiently.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c7816-b8ad-45f7-98b2-892569b81d7c
- billing model shifts the cost of computing power from a capital expense to an operating expense
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 638c7827-cba9-4c3f-9459-852a8eb88259
- eliminates the requirement from users to buy exclusive servers based on the peak load. By sharing network, disk, CPU, memory, and other resources, the pay-as-you-go model only indicates the resources that applications actually used [1, 2, 26], no matter whether the instances are running or idle.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: purple
  id:: 638c7841-45d5-4ea0-8eff-2b3288b50c14
- Nowadays the serverless computing is commonly applied in backend scenarios for batch jobs, including data analytics (e.g., distributed computing model in PyWren [64]), machine learning tasks (e.g., deep learning) [78, 111 ], and event-driven web applications.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 638c78b2-48b0-498c-89b7-d99418eff88d
- [:span]
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 638cb398-2b8c-48a5-8ed3-2e4f0faa91ec
  hl-type:: area
  hl-stamp:: 1670165398686
- s a result, researchers and serverless vendors may find it struggling to grasp and comprehend each issue in the real serverless architecture. In the lack of systematic knowledge, challenges and proposed solutions will lack high portability and compatibility for various serverless systems.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 6395fb09-ad5b-41a9-84cc-8cb3bc8bc5de
- this survey is inspired to propose a layered design and summarize the research domains from different views
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 6395fb78-d0e2-46ee-a616-974ab84cda2f
- help researchers and practitioners to further understand the nature of serverless computing
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 6395fb85-cd3a-49bd-8658-759d12406545
- Virtualization layer
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63a90973-a4b2-4d69-8a0e-181030aef848
- enables function isolation within a performance and functionality secured sandbox
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63a9097d-2096-4c62-a974-ad92b7923549
- sandbox serves as the runtime for application service code, runtime environment, dependencies, and system libraries.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: blue
  id:: 63a90996-ebdd-442a-a788-e4c3495ddf8d
- cloud vendors usually adopt containers/virtual machines to achieve isolation
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63a909aa-7044-49b4-9002-bb49c20141f6
- popular sandbox technologies are Docker [ 41], gVisor [ 49], Kata [67], Firecracker [ 3], and Unikernel [86]
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63a909b4-6ad4-4a28-b7c7-8a0d41d361e6
- Encapsule layer
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fcc4-fbd9-46ea-8744-1f4fa6fca58a
- Various middlewares in the Encapsule layer enable customized function triggers and executions, and they also provide data metrics collection for communicating and monitoring.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fd47-2a8d-4b6c-945e-0a034236474f
- all these additional middlewares the sidecar
  ls-type:: annotation
  hl-page:: 4
  hl-color:: blue
  id:: 63b2fd80-a930-4163-9804-f41a1ce03df6
- It separates the service’s business logic and enables loose coupling between the functions and the underlying platform
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fd92-6428-4fbf-80f4-3bf9ef53e7b1
- the prewarm pool is commonly used in the Encapsule layer [44 , 97, 104, 105 ].
  ls-type:: annotation
  hl-page:: 4
  hl-color:: green
  id:: 63b2fdb7-a478-4c0a-b2c1-910850298ec5
  hl-stamp:: 1672675025923
- to speed up instance startup and initialization
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fde1-7a83-474a-90b6-dd5401efb5ac
- use prediction by analyzing the load pattern to prewarm each by one-to-one approach [118 , 146 ],
  ls-type:: annotation
  hl-page:: 4
  hl-color:: green
  id:: 63b2fdf0-a8dc-4173-acc5-e8e1ef5db9ac
  hl-stamp:: 1672675027327
- build a template for all functions to dynamically install requirements (REQs) according to the runtime characteristics by a one-for-all approach
  ls-type:: annotation
  hl-page:: 4
  hl-color:: green
  id:: 63b2fdf8-8a74-4206-bd1d-a927f6e23d4f
  hl-stamp:: 1672675028808
- System Orchestration layer
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fe0d-e025-4f43-b37a-5acd4ac734c0
- allows users to configure triggers and bind rules
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fe58-082b-48c3-a7e9-e9ebbf06cb25
- ensuring the high availability and stability of the user application by dynamically adjusting as load change
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2fe63-2fe2-4e5e-b1dd-57ad991f9aa7
- Through the cloud orchestrator, the combination of online and offline scheduling can avoid resource contention, recycle idle resources and ease the performance degradation for co-located functions.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: green
  id:: 63b2fea7-f922-4c94-b3c4-097bcec889a9
  hl-stamp:: 1672675034068
- While in the serverless system, resource monitor, controller, and load balancer are consolidated to resolve scheduling challenges [ 4, 32, 50, 57, 66, 70, 88, 139 ]
  ls-type:: annotation
  hl-page:: 4
  hl-color:: purple
  id:: 63b2fefa-ed04-4234-9bc2-2f03794d307c
- scheduling optimizations in three different levels: 
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2ff17-3c80-417d-991a-a93b162b34c5
- esource-level,
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2ff27-3e78-47a8-aa6b-fa7425b934fe
- nstance-level
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2ff31-8da6-4ca3-8a91-cb22ea0382c4
- application-level
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2ff38-359b-4094-ad30-8583911ad2a9
- System Coordination layer
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 63b2ff4d-2305-48ea-8ed9-eb4b4f9db5d0
- consists of a series of Backendas-a-Service (BaaS) components that use unified APIs and SDKs to integrate backend services into functions.
  hl-page:: 4
  ls-type:: annotation
  id:: 63b2ffb5-e46e-4c21-88a9-5cc58c020b1b
  hl-color:: yellow
- t differs from the traditional middlewares that use local physical services outside the cloud.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 63b2ffe2-9e1e-45d1-ad30-95cb448091ca
- provide the **storage**, **queue service** [94, 99], **trigger binding** [75,77], **API gateway,** **data cache** [ 6, 7 ], **DevOps tools** [ 24, 25, 63 , 122 ], and other customized components for better meeting the System Orchestration layer’s **flexibility** requirements.
  hl-page:: 5
  ls-type:: annotation
  id:: 63b2fffa-b6ca-476c-93af-b8f9ff18374c
  hl-color:: blue