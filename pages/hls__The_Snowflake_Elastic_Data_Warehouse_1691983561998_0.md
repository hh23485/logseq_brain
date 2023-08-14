file-path:: ../assets/The_Snowflake_Elastic_Data_Warehouse_1691983561998_0.pdf

- At the same time, the Software-as-a-Service (SaaS) model brings enterprise-class systems to users who previously could not afford such systems due to their cost and complexity
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d99eff-3e94-442b-b86b-1cc2275cee1e
- they have been designed for fixed resources and are thus unable to leverage the cloud’s elasticity. For another thing, their dependence on complex ETL pipelines and physical tuning is at odds with the flexibility and freshness requirements of the cloud’s new types of semi-structured data and rapidly evolving workloads
  ls-type:: annotation
  hl-page:: 1
  hl-color:: red
  id:: 64d99f1a-62ea-4682-8d4e-3c0050e6c53b
  hl-stamp:: 1691983762503
- build an enterprise-ready data warehousing solution for the cloud
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d99f29-c136-4c55-baf8-381bc95d091a
- Snowflake
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d99f30-9551-4d0d-855b-fe2ebb06ed89
- Snowflake is a multi-tenant, transactional, secure, highly scalable and elastic system with full SQL support and built-in extensions for semi-structured and schema-less data
  ls-type:: annotation
  hl-page:: 1
  hl-color:: green
  id:: 64d99f40-f6e9-49ca-bd94-0468a323d944
  hl-stamp:: 1691983788483
- a pay-as-you-go servic
  ls-type:: annotation
  hl-page:: 1
  hl-color:: blue
  id:: 64d99f4d-c8f9-4042-b082-9efc8cde1fe2
- in the Amazon cloud
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d99f51-bf39-445b-a2b7-106b3af5289d
- upload their data to the cloud and can immediately manage and query it using familiar tools and interfaces
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d99f5c-6257-4ce0-ad49-98ffcf172102
- move away from software delivery and execution on local servers
  ls-type:: annotation
  hl-page:: 1
  hl-color:: red
  id:: 64d9a02b-a171-43ad-92eb-9a748567cf0a
  hl-stamp:: 1691983984535
- toward shared data centers and software-as-a-service solutions hosted by platform providers such as Amazon, Google, or Microsoft.
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d9a034-9573-4b7c-b57b-362873417c9c
- unpredictable usage demands
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d9a043-4946-4a6d-8ced-1da7b494df12
- These advantages can only be captured if the software itself is able to scale elastically over the pool of commodity resources that is the cloud
  hl-page:: 1
  ls-type:: annotation
  id:: 64d9a057-5e4e-4b4b-b005-3d8f572ec0c3
  hl-color:: blue
- Traditional data warehousing solutions pre-date the cloud. They were designed to run on small, static clusters of well-behaved machines, making them a poor architectural fit
  ls-type:: annotation
  hl-page:: 1
  hl-color:: red
  id:: 64d9a07d-b7b0-4ce7-8d06-2d3fd7a7e74e
- The structure, volume, and rate of the data were all fairly predictable and well known
  ls-type:: annotation
  hl-page:: 1
  hl-color:: yellow
  id:: 64d9a0a7-8b22-477f-a399-e840c9860a84
- with the cloud, a significant and rapidly growing share of data comes from less controllable or external sources: application logs, web applications, mobile devices, social media, sensor data (Internet of Things)
  ls-type:: annotation
  hl-page:: 1
  hl-color:: blue
  id:: 64d9a0bb-8655-4171-aa49-163628f9500a
  hl-stamp:: 1691984156368
- In addition to the growing volume, this data frequently arrives in schema-less, semi-structured formats
  ls-type:: annotation
  hl-page:: 1
  hl-color:: blue
  id:: 64d9a131-aacb-483f-bb35-d552c5d843f9
- Traditional data warehousing solutions are struggling with this new data
  ls-type:: annotation
  hl-page:: 1
  hl-color:: red
  id:: 64d9a139-4e22-497e-b02b-2007b5498305
- we decided to build a completely new data warehousing system specifically for the cloud
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a1c1-2834-4692-86fc-1579a9a5f5d5
- Snowflake is not based on Hadoop, PostgreSQL or the like.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 64d9a1e0-6215-4dd7-b9ed-0847cf9164d5
- key features of Snowflake 
  ls-type:: annotation
  hl-page:: 2
  hl-color:: green
  id:: 64d9a1f4-ef10-4e97-bae7-e42a684050d6
  hl-stamp:: 1691984378131
- Pure Software-as-a-Service (SaaS) Experience
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a200-f085-4cde-88b6-80ae14331f25
- Relational
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a205-792f-44fb-a5cf-85760d8fbada
- Semi-Structured
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a20a-5eb4-4ac7-9227-65ef914584bc
  hl-stamp:: 1691984398843
- Elastic
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a216-689d-423f-aeab-fe352c04910d
- Highly Available
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a21b-60e4-49c2-97c4-8420daf4c774
- Durable
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a21f-276b-4b11-96cb-42e8dee925c3
- Cost-efficient
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a224-81cc-4fae-935c-e8badd8e5c5a
- Secure
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a228-5ff2-489f-b29f-3060e771f345
- Users need not buy machines, hire database administrators, or install software
  ls-type:: annotation
  hl-page:: 2
  hl-color:: green
  id:: 64d9a555-6eb3-476f-b38f-8bb8bcf501fa
- can then immediately manipulate and query their data using Snowflake’s graphical interface or standardized interfaces such as ODBC
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a561-2be8-40ce-b174-c736e4cbe888
- offers built-in functions and SQL extensions for traversing, flattening, and nesting of semi-structured data
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a584-df18-49d6-b98b-7bc8228bcf2d
- popular formats such as JSON and Avro
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a58b-f065-42e9-88b9-a695b01f0183
- Automatic schema discovery and columnar storage make operations on schema-less, semi-structured data nearly as fast as over plain relational data, without any user effort.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a59c-d407-4717-82d1-b76d29f38c80
- Storage and compute resources can be scaled independently and seamless
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a5aa-9290-4baf-b1df-06b9b53669f6
- Tables are horizontally partitioned across nodes and each node is only responsible for the rows on its local disks.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a744-cd24-4648-9369-48aa444238ea
- A pure sharednothing architecture has an important drawback though: it tightly couples compute resources and storage resources, which leads to problems in certain scenarios.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9a793-1004-498b-97fc-2bc44f870ac3
- Shared-nothing architectures have become the dominant system architecture in high-performance data warehousing
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a7b7-d1a3-4f36-afd5-f5724e206a25
- Heterogeneous Workload
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a8db-ed75-4e2c-9d16-bc1b9fed5b3e
- Membership Changes
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a8de-3d62-4816-8fa6-ff3a04ddea09
- Online Upgrade
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a8e0-61a1-4741-b384-cf262a2d6f43
- the hardware is homogeneous, the workload typically is not
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9a8ed-c0a3-4998-a21c-8868229cbe31
- poor fit for complex queries(low I/O bandwidth, heavy compute) and vice versa.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: red
  id:: 64d9a8fc-1a98-402c-be26-72e92d3945a1
- the hardware configuration needs to be a trade-off with low average utilization.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a917-4089-48c1-9af9-d41e7c2e8481
- large amounts of data need to be reshuffled.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a92d-77e4-4dc8-a2ac-99dff6472280
- very same nodes are responsible for both data shuffling and query processing, a significant performance impact can be observed, limiting elasticity and availability.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a947-046e-4bc6-ba1f-6ca3cdbca067
- software and hardware upgrades eventually affect every node in the system.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a966-ce2a-4afb-8fea-301695645d43
- but is made very hard by the fact that everything is tightly coupled and expected to be homogeneous.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a975-5838-480f-abe1-35f28e6dc957
- The situation is very different in the cloud
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 64d9a9b0-d903-4264-b320-5de3b9200831
  hl-stamp:: 1691986599797
- Platforms such as Amazon EC2 feature many different node types
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 64d9a9b6-c37f-4dd1-95df-18f0e2390756
- node failures are more frequent and performance can vary dramatically, even among nodes of the same type
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 64d9a9c5-ae45-4460-9bdd-1e67fc91743c
  hl-stamp:: 1691986601823
- Membership changes are thus not an exception, they are the norm
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 64d9a9cc-282f-4cfa-aec9-f4eddb0afbf0
  hl-stamp:: 1691986603484
- there are strong incentives to enable online upgrades and elastic scaling
  ls-type:: annotation
  hl-page:: 2
  hl-color:: blue
  id:: 64d9a9db-ceeb-442e-8701-5762c8567e6f
  hl-stamp:: 1691986604779
- Snowflake separates storage and compute
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9a9f0-5ab6-4763-bbd1-922f20aa38b9
- Compute is provided through Snowflake’s (proprietary) shared-nothing engine
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9a9fe-8bfd-4c84-a1b5-81b4d0959bc8
- Storage is provided through Amazon S3 [5], though in principle any type of blob store would suffice (Azure Blob Storage [18, 36], Google Cloud Storage [20])
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa09-4793-4a2e-9fff-fc30b0f4eb5c
- each compute node caches some table data on local disk.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa1a-bf22-441d-bc10-31ac0707ac2c
- ocal disk space is not spent on replicating the whole base data, which may be very large and mostly cold (rarely accessed)
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa2a-e5f3-4254-840e-7e43c0fd3852
- local disk is used exclusively for temporary data and caches, both of which are hot (suggesting the use of high-performance storage devices such as SSDs).
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa38-94e8-4def-96dd-2bd85a2e9e01
- once the caches are warm, performance approaches or even exceeds that of a pure shared-nothing system
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa41-c50a-44a9-a4e4-83e3e21669f4
- multi-cluster, shared-data architecture.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa4c-0c13-4199-9dad-d7bfd5320e25