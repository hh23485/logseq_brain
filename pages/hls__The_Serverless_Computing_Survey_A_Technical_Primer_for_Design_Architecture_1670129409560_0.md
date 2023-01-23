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
- Whenever a user function is invoked in serverless computing, it will be loaded and executed within a virtualized sandbox
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44e28-a2d7-49ab-9f6d-8e4a12aba803
- A function can either reuse a warm sandbox or create a new one, but usually not co-run with different user functions.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44e50-0f48-4715-b202-24a91d7e136b
- most of the concerns in virtualization are isolation, flexibility, and low startup latency.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 63b44e83-c471-49b4-b335-5d8467a50064
- solation ensures that each application process runs in the demarcated resource space, and the running process can avoid interference by others.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44ea0-fbb6-42bf-a4c6-f971f2a9b424
  hl-stamp:: 1674444799729
- The flexibility is demonstrated by the ability of testing and debugging, and the additional supports for extending over the system
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44eac-b5de-4b19-8a9f-66e5f194a684
- Low startup latency requires a fast response for the sandbox creation and initialization
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44eb8-3c0d-4c25-8caa-634b3efc77e2
- traditional VM (Virtual Machine),
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44f38-eb11-48d7-a358-768867ca1570
- container
  hl-page:: 5
  ls-type:: annotation
  id:: 63b44f41-828a-49ec-957a-9ed4a6ee3da6
  hl-color:: yellow
- secure container
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44f48-3f10-4543-aa9f-526b11cc6bf0
- Unikernel.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63b44f4d-04a5-4642-bcbf-39462ec691bc
- [:span]
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63bcb80f-53d8-4720-b605-59bf86249633
  hl-type:: area
  hl-stamp:: 1673312269240
- the response latency of cold startup
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63c36535-ef11-43fe-a231-2773cbe338b3
- Isolation level
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63c36540-2216-455c-ba20-4d96dfd58119
- the capacity of functions running without interference by others
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63c3654b-64bb-4d23-827d-362f09e7be84
- OSkernel
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63c3657a-888c-4570-8654-eb38318564a0
- whether the kernel in GuestOS is share
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63c36582-2ee3-47f8-ab9f-af8d98bbb4dd
- . “Hotplug” allows the function instance to start with minimal resources (CPU, memory, virtio blocks) and add additional resources at runtime
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce02eb-5dc9-4bcc-af80-1af703b53b04
- “OCI supported” means whether it provides the Open Container Initiative (OCI), an open governance structure for expressing container formats and runtimes
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce0309-268d-46e3-906b-ce46d2f124aa
- traditional VM-based isolation adopts a VMM 
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1aa2-5fab-4cdb-befc-608dd31faec0
- provides virtualization capabilities to GuestOS.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1af2-36f3-47db-be21-01261dca4a97
- mediate access to all shared resources by provided interfaces (or using Qemu/KVM
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1b12-929d-4eab-beaa-1675587969ff
- shows high flexibility in quick failsafe when patch performing on applications within each VM instance
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1b24-37b7-4261-aa82-d52f384fb96f
- lacks the benefits of lower startup latency for user applications (usually >1000ms)
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1b37-5a25-4e4f-be27-180b443b16c4
- This tradeoff is fundamental in the serverless computing, where functions are small while the relative overhead of VMM and guest kernel is high
  ls-type:: annotation
  hl-page:: 5
  hl-color:: red
  id:: 63ce1b76-31ae-417f-846c-8e9e18d7978b
- Container 
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1c7c-baef-421c-affd-f40c160725db
- The container engine leverages the Linux kernel to isolate resources, and creating containers as different processes in HostOS [19, 92 ]
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1c90-3034-44be-9341-3c25225ff81d
- shares the HostOS kernel with the read-only
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 63ce1ca3-5672-4deb-80ea-93cdae538498
- typically includes binaries and libraries
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1cc2-daae-4b91-9fd4-3c55ae86afbe
- with the UnionFS (Union File System), which enables the combination of the layered container image by read-only and read-write layers
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1ced-3ab9-4990-94ed-9a0d92c9d077
- achieves the isolation through namespace to enable processes sharing the same system kernel and Linux Cgroups to set resource limits
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1d15-1ba3-425c-a73a-9bd8c5e91202
- Without hardware isolation, container-based sandboxing shows lower startup latency than coarse-grained consolidation strategies [11, 147] in hypervisor-based VMs
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1d27-b043-4159-98ec-c627127f3027
- Docker packages software into a standardized RunC container adapted to the environment requirements, including libraries, system tools, code, and runtime
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1d92-82ec-4e72-b705-10e8891e9517
- has been widely applied to various serverless systems for its lightweight nature.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1e62-6606-4d2f-aba9-82863e82be66
- SOCK [101 ] proposes an integration solution for serverless RunC containers, where redundant mechanisms in Docker containers are discarded in this lean container
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 63ce1e7e-f020-419f-bced-6aaf326170bc
  hl-stamp:: 1674452659425
- SOCK container makes serverless systems running more efficiently in startup latency and throughput.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 63ce1eac-2c24-4019-8713-b8df7734a198
- By only constructing a root file system, creating communication channels, and imposing isolation boundaries
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1f00-b15e-4eb8-94bf-3052f0c55a96
- startup latency of SOCK container is reduced to 10ms50ms, comparing to docker containers that usually takes 50ms-500ms
  ls-type:: annotation
  hl-page:: 6
  hl-color:: green
  id:: 63ce1f30-ff66-4713-aef1-da6b9152e9cb
- CNTR [130] splits the container image into “fat” and“slim” parts.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1f7e-3991-421e-829d-58446efbfa52
- A user can independently deploy the “slim” image and expand it with additional tools by dynamically attaching the “fat” image to it. 
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce1fa7-4f87-44d7-bbce-9c11a904c87c
- can significantly improve the overall performance and effectively reduce the image size when extensively applied in the data center.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: green
  id:: 63ce1fbe-6962-4394-9812-e5a845312218
- additional tools (e.g., debuggers, editors, coreutils, shell) enriching the container and increasing the image size
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 63ce1fd8-9ea8-4670-8b1f-1f50e60f83d0
- security concerns in Virtualization Layer arise for the relatively low isolation level of containers
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 63ce2062-a2ea-4787-abc5-f479012ab609
- It requires containers to prevent code vulnerabilities in the case of shared kernel architecture.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce20d8-e3ac-4e55-9c3f-70123e608d9c
- Side-channel attacks such as Meltdown [ 84], Zombieload [114 ], Spectre [72] prompt mitigation approaches toward vulnerabilities, especially for multi-tenants in serverless context
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 63ce2149-1cfa-4288-ab46-46d56f0932f2
- should concern with preventing privilege escalation, information, and communication disclosure side channels [3].
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 63ce21ae-414d-4338-89e2-cc4e6ac2e758
- leveraging Secure Container.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce21ec-88b8-44f9-9068-06121a78a193
- Microsoft proposes their Hyper-V Container for Windows [58]
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce2204-f574-48eb-9b77-722837a8603e
- offers enhanced security and broader compatibility.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce2230-4760-4595-bc57-757dc2f89d45
- Each instance runs inside a highly optimized MicroVM and does not share its kernel with others on the same hos
  ls-type:: annotation
  hl-page:: 6
  hl-color:: green
  id:: 63ce2261-63b3-453c-9dc0-c5248b283a84
  hl-stamp:: 1674453613104
- still a heavy-weight virtualization that can introduce more than1000ms of startup latency
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 63ce227a-0502-49b0-a1d1-701233bf740d
- the kernel in it acts as a non-privileged process to restrict syscalls that called in userspace
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce22c7-6733-4ebb-a139-83546771a8c9
- overhead introduced during interception and processing syscalls in a sandbox is high
  ls-type:: annotation
  hl-page:: 7
  hl-color:: red
  id:: 63ce2336-e813-4a45-bf9e-e97add7d0d15
- Google gVisor [49]
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce234b-ccb7-4388-b2ba-708762e5980f
- the kernel in it acts as a non-privileged process to
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 63ce2365-0b9c-43bf-bb40-887a0933b77b
- not well-suited for applications with heavy syscalls.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: red
  id:: 63ce2447-c4e2-4a21-a593-d6abbe3f722f
- FireCracker [ 3] creates MicroVMs by customizing VMM for cloud-native applications. 
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2503-56e7-4128-99ea-3ac31919b5af
- Each Firecracker sandbox runs in user space and is restricted by Seccomp, Cgroup, and Namespace policies
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2522-a91c-4144-a3cb-88ce7ce08aa0
- Kata [67] adopts an agent to communicate with the kata-proxy located on the host through the hypervisor, thus achieve a secure environment in a lightweight manner
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 63ce2555-6c64-4c60-8317-c04b6efee9bc
  hl-stamp:: 1674454361036
- FireCracker and Kata containers can significantly reduce startup latency and memory consumption, and they all need only 50ms-500ms to start a sandbox
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2574-e459-4af6-b975-395febf46906
- provide complete and strong isolation from the HostOS and other tenants, at the cost of the limited flexibility in the condensed MicroVM
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce258c-1db7-4ec2-8615-7b1b15006564
- still results in instances’ long startup latency due to the additional application initialization, e.g., JVM or Python interpreter setup.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce259d-dec4-43ab-be50-22fbb9f6c002
- Specialized Unikernel: enhance flexibility with high security and performance.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce272e-682e-455d-9c01-d0561d82be47
- leverages libraryOS, including series of essential dependent libraries to construct a specialized, single-address-space machine image
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2777-66e1-44e5-86ad-148f3ee51b1e
- runs as a built-in GuestOS, the compile-time invariance rules out runtime management, which significantly reduces the applicability and flexibility of Unikernel.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: red
  id:: 63ce27a1-b57f-4e97-b4df-7147aa890f29
  hl-stamp:: 1674454992693
- unnecessary programs or tools such as 𝑙𝑠, 𝑐𝑑, 𝑡𝑎𝑟 are not contained, so the image size of a Unikernel is smaller 
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 63ce27c1-fda2-4284-952b-c407f421f6f0
- 2MB by mirage-skeleton [ 95] that compiled from Xen)
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 63ce27e1-0299-40a8-a84d-c94670a888f3
  hl-stamp:: 1674455048562
- startup latency is much less (e.g., startup within 10ms)
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 63ce27f3-87c3-4d13-b36d-04b05208dc57
  hl-stamp:: 1674455050126
- the security is more substantial than containers
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 63ce2803-1726-4caf-86ec-910ee1470778
  hl-stamp:: 1674455051698
- LightVM [90 ] replaces the time-consuming XenStore and implements the split tool stack, separating functionality that runs periodically from that which must be carried out, thus improving efficiency and reducing VM startup latency.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2882-ff5e-4731-92fd-01f524825d85
- Olivier proposes HermitTux [ 102], a Unikernel model compatible with Linux binary.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce28ba-5dac-42a3-972a-734e2266aba2
- makes the Unikernel model compatible with Linux Application Binary Interface while retaining the benefits of Unikernel.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 63ce28ca-4633-4247-9d1f-88d135c2e995
- s not adaptable for developers once built, making it inherently inflexible for applications, let alone the terrible DevOps environment
  ls-type:: annotation
  hl-page:: 7
  hl-color:: red
  id:: 63ce28db-d043-4316-8f84-258bef6d959b
- in heterogeneous clusters, the heterogeneity of the underlying hardware forces Unikernel to update as drivers change, making it the antithesis of serverless philosophy.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2dc9-d25f-46e1-a132-b12697da31ba
  hl-stamp:: 1674456543846
- Tradeoffs among Security, performance, and flexibility.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2e47-9149-442e-8c63-bb35ecd7ce23
- [:span]
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 63ce2eaf-920b-4fb7-9b55-3d70b4cb3ccd
  hl-type:: area
  hl-stamp:: 1674456750879
- A cold startup in serverless computing may occur when the function fails to capture a warm running container, or experiences a bursty load
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce3210-7c84-4e90-969e-139149ef4554
- a function is invoked for the first time, or scheduled with a longer invocation interval than the instance lifetime
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce3299-3fc0-462b-afe6-8ec239372fad
- instances (or pods) must get started from scratch
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce32ae-ad78-4e71-aa98-673aa9033bd8
- instances need to perform horizontal scaling during a surge in user workloads
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce32bc-7914-4018-a0c6-6871106a3cf6
- autoscale as load changes to ensure adequate resource allocation
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce32d9-abe1-4868-94bf-8969b2f49c5c
- Besides taking less than one second to prepare a sandbox in the Virtualization layer, the initialization of software environment, e.g., load Python libraries; and application-specific user code can dwarf the former [42, 65, 83, 101 , 117].
  ls-type:: annotation
  hl-page:: 8
  hl-color:: red
  id:: 63ce3d22-8a9e-479c-b016-9aac95d0a404
  hl-stamp:: 1674461524919
- an efficient solution is to prewarm instances in the Encapsule layer. This approach is known as the prewarm startup
  ls-type:: annotation
  hl-page:: 8
  hl-color:: green
  id:: 63ce4064-41b1-4592-804e-023190c9880a
  hl-stamp:: 1674461531794
- [:span]
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce407f-e3d2-4efe-98ff-3869a6cf67ca
  hl-type:: area
  hl-stamp:: 1674461310047
- “Template” reflects whether the cold startup instance comes from a template.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce41f0-2f7a-48d5-9f1e-1b51766532a5
- “Static image” shows whether the VM/container image for prewarm disables dynamically updating in each cold startup
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce41fc-5a15-4717-bd1c-fa85781e3ed8
- “Pool” indicates whether there is a prewarm pool for function cold startups.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce4206-42b4-4b74-87ff-4332d712d84d
- “Exclusive” and “Fixed-size” represents whether the prewarmed instance and its prewarm pool is exclusive and size-fixe
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce420d-b169-4127-bc4a-2bd7f65345cc
- . “Predict/Heuristic” points out whether the prediction algorithm or heuristic-based method is used to prewarm instances
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce4214-89e1-47f6-85ab-cd499f82fb9d
- “REQs” reflects whether the runtime libraries and packages are dynamically loading and updating in the prewarm instance
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce421b-3d71-4696-9840-d6d78499fc28
- “C/R” reflects whether it supports checkpoint and restore to accelerate the startup.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce4221-7373-452c-afe5-097080864d5f
- “Sidecar based” represents whether the relevant technologies can be implemented or integrated into the sideca
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce4225-cbb6-4627-90e7-46d483a7a832
- “Imp” indicates where it is implemented.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 63ce4228-bce8-439a-b869-df458c180666
- one-to-one
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 63ce4dae-34ef-476d-92d7-35d9785e5af1
- onefor-all
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 63ce4db8-58bd-478b-968c-f77afd833d61
- One-to-one prewarm by size-fixed pool: effective but resource-unfriendly.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 63ce4ed8-bf98-4d0c-82a5-ae9fbf845afa
- One-to-one prewarm by predictive warm-up: ways to make resource friendly.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 63ce4edb-fe0f-48bc-9b3f-171d631f7b80