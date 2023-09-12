file:: [Building_An_Elastic_Query_Engine_on_Disaggregated_Storage_1692007378670_0.pdf](../assets/Building_An_Elastic_Query_Engine_on_Disaggregated_Storage_1692007378670_0.pdf)
file-path:: ../assets/Building_An_Elastic_Query_Engine_on_Disaggregated_Storage_1692007378670_0.pdf

- along with a discussion on how recent changes in cloud infrastructure
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fc12-3def-46cd-a8e1-7aac3d03c330
- Using data collected from various components of our system during execution of 70 million queries over a 14 day period, our study both deepens the understanding of existing problems
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fc31-5299-48a1-be84-c97ea1fa7b81
- highlights new research challenges along a multitude of dimensions including design of storage systems and high-performance query execution engines.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fc35-eb9b-4e6a-b44b-c1950ca1a9ba
- presents Snowflake design and implementation
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fc0c-0400-498b-82b6-218e3b6e114f
- Shared-nothing architectures have been the foundation of traditional query execution engines and data warehousing systems
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fc82-e198-4f8f-ba35-ea895f8452a6
- However, these benefits come at the cost of several major disadvantages:
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fc84-c84e-49bc-8739-eade7103c623
  hl-stamp:: 1692007596176
- Hardware-workload mismatch
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fca7-95d8-48eb-9a90-df734ed98117
  hl-stamp:: 1692007594674
- hard to strike a perfect balance between CPU, memory, storage and bandwidth resources provided by compute nodes, and those required by workloads.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fcca-30a6-4306-9f3f-787e151dbb71
- Thus, to meet performance goals, resources usually have to be overprovisioned;
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fce4-7ce1-4dfc-bf8f-0d1050e9b1b3
  hl-stamp:: 1692007655845
- Lack of Elasticity
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fcfc-144a-448a-82f2-f21d28918c95
- queries run by our customers have extremely skewed intermediate data sizes that vary over five orders of magnitude (§4), and have CPU requirements that change by as much as an order of magnitude within the same hour (§7)
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fd4c-9f31-4fa7-8f74-e4ce4ad4a3f7
- shared-nothing architectures do not admit efficient elasticity; the usual approach of adding/removing nodes to elastically scale resources requires large amounts of data to be reshuffled
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fd59-450b-4172-a23a-719eac852c4b
- not only increases network bandwidth requirements but also results in significant performance degradation since the set of nodes participating in data reshuffling are also responsible for query processing
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fd66-cf96-42d3-accd-d976936b20c9
- Traditional data warehousing systems were designed to operate on recurring queries on data with predictable volume and rate
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fd85-2dd6-4686-9b9a-5571957e3b3e
- For such workloads, shared-nothing architectures beget high cost, inflexibility, poor performance and inefficiency, which hurts production applications and cluster deployments.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9fdbf-5d9c-46dd-8b5c-875684fe59ae
- data comes from less controllable, external sources(e.g., application logs, social media, web applications, mobile systems, etc.) resulting in ad-hoc, time-varying, and unpredictable query workloads.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9fdcc-166b-4972-809a-7c6787d259c5
  hl-stamp:: 1692007886346
- Snowflake system design uses two key ideas
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9fef4-b12b-4970-99b2-01d3c7da9b0c
- First, it uses a custom-designed storage system for management and exchange of ephemeral/intermediate data that is exchanged between compute nodes during query execution
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9ff5f-0d9a-4aad-9c42-285c690ba462
- because existing persistent data stores [ 5, 8] have two main limitations:
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9ff96-4c4f-4feb-8bc0-fac1f58232f0
- (1) they fall short of providing the necessary latency and throughput performance to avoid compute tasks being blocks on exchange of intermediate data
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9ff9c-90a0-4522-98f4-8862d478702c
- (2) they provide stronger availability and durability semantics than what is needed for intermediate data
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9ffbd-71e9-4411-9d23-38d5a5c81acd
- Second, Snowflake uses its ephemeral storage system not only for intermediate data, but also as a write-through “cache” for persistent data
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9ffef-d501-4396-b7f1-1d7f5924f317
- Combined with a custom-designed query scheduling mechanism for disaggregated storage, Snowflake is able to reduce the additional network load caused by compute-storage disaggregation as well as alleviate the performance overheads of reduced data locality.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: green
  id:: 64da0061-a8c1-448c-be16-a59e917d7854
- focus on ephemeral storage system design, query scheduling, elasticity and efficiently supporting multi-tenancy. 
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0071-f958-4e02-af30-3da9a3372e8f
- present a detailed study of network, compute and storage characteristics in Snowflake.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0087-1a43-4033-9a86-4a05868c10a1
- Customers submit a wide variety of query types
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0090-8084-48de-88dc-b968d7b64182
- Even with a small amount of local storage capacity, skewed access distributions and temporal access patterns common in data warehouses enable reasonably high average cache hit rates ( 60 -80% depending on the type of query) for persistent data accesses.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da00a6-98d1-42a1-b5f4-957bdafd7bc8
- Several of our customers exploit our support for elasticity(for ∼20% of the clusters).
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da00ac-2299-4923-9ba3-ac616eb7b3f0
- While the peak resource utilization can be high, the average resource utilization is usually low. 
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da00b4-ad84-4579-95ef-019ff695c2df
- Intermediate data sizes can vary over multiple orders of magnitude across queries
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da00db-dd86-48f8-9eeb-e65e41af2968
- the number of compute nodes in their cluster can change by as much as two orders of magnitude during the lifetime of the cluster.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0107-7abc-41fa-8b76-93943f18cddc
- as well as highlights several interesting venues for future research:
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0112-2473-45f3-bc13-dc585281ac6d
- Decoupling of compute and ephemeral storage:
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0115-c256-4ba3-93d6-b430d1693e97
- Deep storage hierarchy:
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0118-5164-4fab-8d45-aec3991d7fda
- Pricing at sub-second timescales:
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da011c-b338-4bdb-8715-67e67fd4c594
- existing mechanisms for improving caching and data locality were designed for two-tier storage systems (memory as the main tier and HDD/SSD as the second tier).
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0e7d-9646-4f6e-b952-72c68f2e6369
- the storage hierarchy in our production clusters is getting increasingly deeper, and new mechanisms are needed that can efficiently exploit the emerging deep storage hierarchy.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 64da0e84-27e0-43a5-88fc-52432b923e31
- most cloud providers have recently transitioned to sub-second pricing [ 6 ], leading to new technical challenges in efficiently achieving resource elasticity and resource sharing across multiple tenants
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 64da0f18-2377-446a-88d5-3104c401af7d
  hl-stamp:: 1692012345067
- This paper focuses on Snowflake system architecture along with compute, storage and network characteristics observed in our production clusters
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64da0fdf-804e-4783-ba11-cf98871ca078
- releasing an anonymized version of the dataset used in this paper; this dataset comprising statistics collected per-query for ∼70 million queries.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da0ff4-dc7e-4259-ba66-43546349dc21
- prominent 
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1021-f61b-45e2-91a6-d757dae8d06d
- nevertheless 
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1036-f696-410f-bd57-f808513713e9
- 2 Design Overview
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1079-c352-4480-8df3-658789ad955a
- Snowflake treats persistent and intermediate data differently
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da10f0-08fc-4246-891b-ad1fa6347c64
- followed by a high-level overview of Snowflake architecture 
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da10f6-78b3-458a-8639-3e6487e72dfb
- query execution process
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da10f9-82fd-4d5e-ae1f-5e6fcc4c4926
- 2.1 Persistent and Intermediate data
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da10fd-1b68-4602-984d-b96a2e0a5d78
- Persistent data is customer data stored as tables in the database
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1145-f04b-4e91-a146-8ef1a96e4881
- Snowflake has three forms of application state
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1152-446c-4834-8b44-4b45ec7c24dc
- Intermediate data is generated by query operators (e.g., joins) and is usually consumed by nodes participating in executing that query
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1168-3312-42df-b6a6-1e25601818dc
- to avoid nodes being blocked on intermediate data access, low-latency high-throughput access to intermediate data is preferred over strong durability guarantees.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1183-0978-4b79-a27a-00ec0d07f4ad
- Metadata such as object catalogs, mapping from database tables to corresponding files in persistent storage, statistics, transaction logs, locks, etc
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da11d5-085a-4b15-994c-252faaa9f218
- 2.2 End-to-end System Architecture
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1223-c4b2-4795-9ce3-c49d50fc4322
- high-level architecture for Snowflake
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1241-da5e-419a-aa06-4ffa204d918e
- [:span]
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1250-b212-40b3-a742-cab379616765
  hl-type:: area
  hl-stamp:: 1692013135799
- Centralized Control via Cloud Services.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da12a5-f340-4773-baaa-0941a0c1a38f
- Elastic Compute via Virtual Warehouse abstraction
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da12b0-99f8-4067-855d-021d07bc4062
- Elastic Local Ephemeral Storage
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da12b5-0b37-4275-b31e-ebed5444766c
- Elastic Remote Persistent Storage
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da12bc-f2c6-49e6-9436-6a6a14b8e099
- This layer is responsible for access control, query optimization and planning, scheduling, transaction management, concurrency control, etc.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da12dd-6518-4f04-8c9d-03cdc6f4e6ad
- CS is designed and implemented as a multi-tenant and long-lived service with sufficient replication for high availability and scalability.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da12f1-2187-4cd4-8c9c-9a422ba854cd
- Each VW is essentially a set of AWS EC2 instances on top which customer queries execute in a distributed fashion.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da1334-f3e7-4a30-b3e8-2f0531e0d82f
- Customers pay for compute-time based on the VW size
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da133f-f41d-4071-826d-b70122922859
- To support elasticity at fine-grained timescales (e.g., tens of seconds), Snowflake maintains a pool of pre-warmed EC2 instances; upon receiving a request, we simply add/remove EC2 instances to/from that VW (in case of addition, we are able to support most requests directly from our pool of pre-warmed instances thus avoiding instance startup time)
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da137e-7c1c-41c0-a8b4-95df7eb6445c
- Each VW may run multiple concurrent queries. In fact, many of our customers run multiple VWs
  ls-type:: annotation
  hl-page:: 4
  hl-color:: yellow
  id:: 64da138f-f7de-47b5-8e58-25c2f2213f70
- built a distributed ephemeral storage system custom-designed to meet the requirements of intermediate data in our system.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da151f-24fe-4a73-9d34-ecb4234320f5
- existing persistent data stores do not meet these requirements (e.g., S3 does not provide the desired low-latency and high-throughput properties 
  ls-type:: annotation
  hl-page:: 4
  hl-color:: red
  id:: 64da152b-4a2e-431b-a3e3-21c25221ad02
  hl-stamp:: 1692013872454
- co-located with compute nodes in VWs, and is explicitly designed to automatically scale as nodes are added or removed
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da1630-8aa3-467b-9096-7557880da722
- Each VW runs its own independent distributed ephemeral storage system which is used only by queries running on that particular VW
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da166a-387e-4149-9ee3-4882be91cca3
- stores all its persistent data in a remote, disaggregated, persistent data store.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da16a4-a654-44d5-9b13-e871cff27bb4
- because of S3’s elasticity, high availability and durability properties.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da16d6-8f4b-4b8c-95c0-e061b588199f
- storing immutable files — files can only be overwritten in full and do not even allow append operations.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 64da16e4-d755-42bf-be28-f4db6a0bc914
- S3 supports read requests for parts of a file
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 64da16f3-c6db-4b5b-9958-e1564f21e805
- To store tables in S3, Snowflake partitions them horizontally into large, immutable files that are equivalent to blocks in traditional database systems
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da1707-d846-4b7a-9106-1a0a7af68e66
- Within each file, the values of each individual attribute or column are grouped together and compressed, as in PAX
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da1b10-98cb-4136-856e-76a1d6b7d8bc
- Each file has a header that stores offset of each column within the file
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da1b1a-3068-42f5-9263-16d79bce9bbf
- enabling us to use the partial read functionality of S3 to only read columns that are needed for query execution
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64da1b27-07bb-4b67-998a-e47d98a8e930
- Query execution begins with customers submitting their query text to CS for execution on a speciﬁc customer VW
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003ac0-c696-43eb-b89b-357969d4d9ab
- CS performs query parsing, query planning and optimization, producing a set of tasks that need to be executed
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003ace-d8c6-4f70-9d05-7b2f5c44fbac
- then schedules these tasks on compute nodes of the VW
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003adb-2416-4e56-9762-6d7c65fac01e
- each task may perform read/write operations on both ephemeral storage system and remote persistent data store
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003aeb-70f4-4b1e-92fe-496cb79b1e99
- CS continually tracks the progress of each query, collects performance counters, and upon detecting a node failure, reschedules the query on compute nodes within the VW
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 65003b25-1bac-4140-b15c-85c6701bb369
- Once the query is executed, the corresponding result is returned back to the CS and eventually to the customer
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003b41-2836-4f64-a8ff-c380f1bee4f5
- Snowﬂake collects statistics at each layer of the system
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003b75-0fde-4454-9c71-d676a959f426
- each individual VW(size over time, instance types, failure statistics, etc.)
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003b92-9d19-429f-8811-04ef9d52c582
- performance counters for individual queries, time spent in different phases of query execution
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003ba0-fc46-4358-b1f9-7657dca0bc58
- Each node collects statistics for ephemeral and persistent store accesses, resource (CPU, memory and bandwidth) utilization characteristics, compression properties, etc.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003bad-6541-4acf-af88-afab37aa9257
- The dataset is publicly available at https://github.com/resource-disaggregation/snowset
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003e92-f04e-4367-ac17-866c8cb21618
- Query Classiﬁcation
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003ea1-2552-4b20-9c63-044af314ece4
- Read-only queries
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003eaa-ef10-45a3-b992-88ab8e60966f
- these queries can vary over nine orders of magnitude
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003edb-7125-4c4d-8858-364f72b5a4ab
- queries contribute to ∼28% of all customer queries
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 65003ee7-3202-4ea2-9218-367ad5def528
- Write-only queries: 
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65003efe-8df3-4019-a383-e613785fda2f
- Queries along the y-axis are the ones that do not read any persistent data
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65003f0c-8adf-448f-acac-31f7d34fec1a
- the amount of data written by these queries can vary over eight orders of magnitude
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65003f1a-7dcd-41ad-aadb-9f1adee8adb0
- These queries contribute to ∼13% of all customer queries, and essentially represent data ingestion queries that bring data into the system
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65003f2c-258f-48e1-96e2-1c27efafe953
- Read-Write (RW) queries
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65003f77-c41c-4bcb-baaf-045781e14e2a
- region in the middle of the plot contains ∼59% of customer queries, and represents queries that both read and write persistent data
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65003f83-31e3-4cfc-bda8-e1b05287a65e
- 4.1 Storage Architecture, and Provisioning
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 650040fd-ad7d-4bdb-a4e6-02f48984c923
- two limitations in existing persistent data stores
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 6500410c-670b-4f60-97cf-b7426c8aec55
- First, they fall short of providing the necessary latency and throughput performance to avoid compute tasks being blocks on intermediate data exchange
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65004117-939a-4cd0-b611-7d454b9b9b44
- Second, they provide much stronger availability and durability semantics than what is needed for intermediate data.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65004120-56e1-4b8f-8977-6f0d1b6f9d64
- two important design decisions in our ephemeral storage system
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65004134-abb6-4083-9bca-3e01321e2d78
- First, rather than designing a pure in-memory storage system, we decided to use both memory and local SSDs
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 6500413d-2114-4211-8c02-ce661ca323f9
- when memory is full, intermediate data is spilled to local SSDs.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65004155-d742-406a-a299-f8f139cfe9f5
- while purely in-memory systems can achieve superior performance when entire data ﬁts in memory, they are too restrictive to handle the variety of our target workloads
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 650041b5-7053-46ff-8f28-10d8b877ed79
- The second design decision was to allow intermediate data to spill into remote persistent data store in case the local SSD capacity is exhausted
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 650041de-a136-4143-8325-a07c9c919c61
- it does not require keeping track of intermediate data location
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65004231-480a-4ee2-9a40-10693b2ad787
- it alleviates the need for explicitly handling out-of-memory or out-of-disk errors for large queries
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 6500423c-6ebd-4f61-ba3f-2639b2a5d8b3
- allows to keep our ephemeral storage system thin and highly performant
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 65004249-ddf3-4655-9e82-09730a82f147
- 4.2 Persistent Data Caching
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 65004289-c2ac-4a81-a8df-3650d0e9dd5a
- a persistent data ﬁle cannot be cached on any node — Snowﬂake assigns input ﬁle sets for the customer to nodes using consistent hashing over persistent data ﬁle name
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 6500433a-bbea-4be1-9fed-3d9f548d37ce
- each node uses a simple LRU policy to decide caching and eviction of persistent data ﬁles
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 6500434b-639f-45cb-a57c-25adc7b3a5b4
- such opportunistic caching of persistent data ﬁles improves the execution time for many queries in Snowﬂake
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 65004361-caad-4cd7-bcd1-b229974a9201
- intermediate data storage is always prioritized over caching persistent data ﬁles
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 65004373-4f86-4ebf-8f3a-49499d584588
- Maintaining the right system semantics
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 650043d5-0952-46b3-b5c0-64f5272c1621
- First, to ensure data consistency, the “view” of persistent ﬁles in ephemeral storage system must be consistent with those in remote persistent data store
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 650043e3-e132-4e02-97a8-9170c191861f
- by forcing the ephemeral storage system to act as a write-through cache for persistent data ﬁles
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 650043f7-6805-43c0-9078-20e426599686
  hl-stamp:: 1694516221294
- Second, consistent hashing of persistent data ﬁles on nodes in a naïve way requires reshufﬂing of cached data when VWs are elastically scaled
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 65004410-7b3c-4055-9f30-f47d37fa80dc
- implement a lazy consistent hashing optimization in our ephemeral storage system that avoids such data reshufﬂing altogether
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 65004429-4db1-479f-83af-be51d29c598a
- it may be better to prioritize caching a persistent data ﬁle that is going to be accessed by many queries over intermediate data that is accessed by only one
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 650044a3-9474-4aa7-9db8-c7d8cbb0f0dd
- Second, existing caching mechanisms were designed for two-tier storage system
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 650044b4-8e99-4dd0-8b1a-c6b4dbab641e
  hl-stamp:: 1694516483737
- we already have three tiers of hierarchy with compute-local memory, ephemeral storage system and remote persistent data store
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 650044c1-f336-4594-bc81-26643a3eaddd
- to efﬁciently exploit the deepening storage hierarchy, we need new caching mechanisms that can efﬁciently coordinate caching across multiple tiers
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 650044de-b62a-4cd9-895e-577770e4b329
- Future Directions
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 650044f1-4a76-4771-885e-0fdda5d2b67a
- First, since end-to-end query performance depends on both, cache hit rate for persistent data ﬁles and I/O throughput for intermediate data, it is important to optimize how the ephemeral storage system splits capacity between the two
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 65004500-3d1a-4e9d-a957-08078578865f
- high cache hit rates (avg. hit rate is close to 80% for read-only queries and around 60% for read-write queries).
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 65004519-801c-4203-a12b-68298c62aa19
- [:span]
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 65004538-cbdb-4614-a032-5a425bb4f37f
  hl-type:: area
  hl-stamp:: 1694516531537
- the storage hierarchy in the cloud will get increasingly deeper
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 6500455a-3a75-4906-bfa0-685576939981
- Locality-aware task scheduling
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 65004591-9aa0-4899-8502-099d9a3a061f
- To fully exploit the ephemeral storage system, Snowﬂake colocates each task with persistent data ﬁles that it operates on using a locality-aware scheduling mechanism
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 650045b1-c352-4a32-b6ba-80a864b8c3dd