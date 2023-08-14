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
  hl-color:: green
  id:: 64d9a9f0-5ab6-4763-bbd1-922f20aa38b9
  hl-stamp:: 1691986617399
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
- local disk space is not spent on replicating the whole base data, which may be very large and mostly cold (rarely accessed)
  hl-stamp:: 1691986664298
  hl-page:: 3
  ls-type:: annotation
  id:: 64d9aa2a-e5f3-4254-840e-7e43c0fd3852
  hl-color:: green
- local disk is used exclusively for temporary data and caches, both of which are hot (suggesting the use of high-performance storage devices such as SSDs).
  ls-type:: annotation
  hl-page:: 3
  hl-color:: green
  id:: 64d9aa38-94e8-4def-96dd-2bd85a2e9e01
  hl-stamp:: 1691986662782
- once the caches are warm, performance approaches or even exceeds that of a pure shared-nothing system
  ls-type:: annotation
  hl-page:: 3
  hl-color:: green
  id:: 64d9aa41-c50a-44a9-a4e4-83e3e21669f4
  hl-stamp:: 1691986657255
- multi-cluster, shared-data architecture.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: yellow
  id:: 64d9aa4c-0c13-4199-9dad-d7bfd5320e25
- All queries issued by users pass through the Cloud Services layer
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9ca33-3a04-4545-a565-de2903d8dcd4
- all the early stages of the query life cycle are handled
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9ca4d-d70b-48f6-b7d9-6158430cdfab
- query optimizer follows a typical Cascadesstyle approach
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9ca5d-e523-4ef7-8ef3-24c22d22257f
- top-down cost-based optimization
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9ca63-9826-4177-998c-9e4bd1a501ee
- All statistics used for optimization are automatically maintained on data load and updates
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9ca6e-c28e-4af1-a3b8-cf733652c8ca
- does not use indices (cf. Section 3.3.3), the plan search space is smaller than in some other systems.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9ca8d-e09e-47f5-9b76-a4eb7f028e88
- plan space is further reduced by postponing many decisions until execution time,
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d2ef-5558-470b-a7a5-b68dacf71054
- reduces the number of bad decisions made by the optimizer, increasing robustness at the cost of a small loss in peak performance
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d2ff-3f26-4f82-a99b-ce38f6bb82ef
- akes the system easier to use (performance becomes more predictable)
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d321-e7c1-4587-b67d-f6b36ef83d62
- Once the optimizer completes, the resulting execution plan is distributed to all the worker nodes that are part of the query
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d32a-364e-4180-810b-e1c3ca98f045
- As the query executes, Cloud Services continuously tracks the state of the query to collect performance counters and detect node failures
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d33c-32f3-4960-9956-54565add4ac1
- query information and statistics are stored for audits and performance analysis.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d347-d104-434f-90e3-8c7569c12532
- Users are able to monitor and analyze past and ongoing queries through the Snowflake graphical user interface.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d350-a871-4bbf-90da-15cbb651542c
- As mentioned previously, concurrency control is handled entirely by the Cloud Services layer.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d367-49cd-40fa-a35b-f393b6696c6d
- decided to implement ACID transactions via Snapshot Isolation
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d386-4cab-4af1-9d67-10dadb982433
- all reads by a transaction see a consistent snapshot of the database as of the time the transaction started.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d38e-91b3-433c-8de1-c7337e13c0fa
- SI is implemented on top of multi-version concurrency control (MVCC), which means a copy of every changed database object is preserved for some duration
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d396-2bcb-4d01-9b9f-720b98f84312
- Changes to a file can only be made by replacing it with a different file that includes the changes3.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d3a7-dcc1-4def-8c99-2a4accde6fe9
- write operations (insert, update, delete, merge) on a table produce a newer version of the table by adding and removing whole files relative to the prior table version.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d3ba-bf51-4e84-8337-fa77b5adde75
- File additions and removals are tracked in the metadata
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d3c8-c78d-421f-8957-b8a6b1bd2f94
- global key-value store
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d3d0-9eb3-4b4d-b19d-021e17800b3b
- in a form which allows the set of files that belong to a specific table version to be computed very efficiently.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d3da-ee00-408c-b8ae-b12c3bd8ffa1
- Snowflake also uses these snapshots to implement time travel and efficient cloning of database objects
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d3e6-4548-4ba9-aa28-b35332195ddf
- Limiting access only to data that is relevant to a given query is one of the most important aspects of query processing
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9d40b-7fad-4a71-aeec-018e3eae2975
- indices
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e11e-d9a0-4357-a718-f002a9721bbc
- it raises multiple problems for systems like Snowflak
  ls-type:: annotation
  hl-page:: 5
  hl-color:: red
  id:: 64d9e156-3f2f-4f25-9866-d3fc522f50c4
  hl-stamp:: 1692000652027
- . First, it relies heavily on random access, which is a problem both due to the storage medium(S3) and the data format (compressed files)
  ls-type:: annotation
  hl-page:: 5
  hl-color:: red
  id:: 64d9e164-7202-497b-a969-f984b1550a91
  hl-stamp:: 1692000653901
- Second, maintaining indices significantly increases the volume of data and data loading time
  ls-type:: annotation
  hl-page:: 5
  hl-color:: red
  id:: 64d9e16b-b5bd-47cd-9401-a942859e606e
  hl-stamp:: 1692000655424
- Finally, the user needs to explicitly create the indices—which would go very much against the pure service approach of Snowflak
  ls-type:: annotation
  hl-page:: 5
  hl-color:: red
  id:: 64d9e176-802b-4d60-9309-4f7b6bfa8da3
  hl-stamp:: 1692000656625
- Even with the aid of tuning advisors, maintaining indices can be a complex, expensive, and risky process.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 64d9e188-8ab4-40ef-a9ea-339d459e6e0f
  hl-stamp:: 1692000660031
- min-max based pruning,
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e329-a048-4ab1-a892-560b696d920e
  hl-stamp:: 1692001076816
- zone maps
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e32f-9355-4af6-b4ad-d28a040677f4
  hl-stamp:: 1692001078265
- data skipping
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e331-82a8-422c-8ddc-1cec2f6fe3de
  hl-stamp:: 1692001079595
- Here, the system maintains the data distribution information for a given chunk of data (set of records, file, block etc.), in particular minimum and maximum values within the chunk.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e343-1f96-41e5-9418-ab2e6f46a4a1
- imagine files f1 and f2 contain values 3..5 and4..6 respectively
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e35c-988c-44a3-a3ee-afc02f25de8d
- Unlike traditional indices, this metadata is usually orders of magnitude smaller than the actual data, resulting in a small storage overhead and fast access.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e3d9-8614-4d6d-aaa3-28e7a95b62fd
- does not rely on user input
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 64d9e402-521a-4734-adf9-196bae263c72
  hl-stamp:: 1692001395399
- scales well
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 64d9e408-a7e3-4437-a5c2-7bc812b6faea
  hl-stamp:: 1692001396925
- it is easy to maintain
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 64d9e40d-ebe7-4deb-9876-d5e96b3687fb
  hl-stamp:: 1692001398740
- orks well for sequential access of large chunks of data
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 64d9e412-0ea7-46d8-8a9c-05df6103371e
  hl-stamp:: 1692001399986
- adds little overhead to loading, query optimization, and query execution times.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: green
  id:: 64d9e45e-84bc-4211-a071-777b6e46ba8d
  hl-stamp:: 1692001401365
- for every indi-
  ls-type:: annotation
  hl-page:: 5
  hl-color:: yellow
  id:: 64d9e469-c346-4ee8-b508-1d3d034682db
- vidual table file.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e46a-0369-4dc7-80fe-c1a0028031a5
- not only covers plain relational columns,
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e480-05fb-4611-b2f0-af9f0109bc3a
  hl-stamp:: 1692001415997
- also a selection of auto-detected columns inside of semi-structured data,
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e486-4b18-4cc2-a903-4df86e09cd88
  hl-stamp:: 1692001417174
- The optimizer performs pruning not only for simple base-value predicates, but also for more complex expressions such as WEEKDAY(orderdate) IN (6, 7).
  ls-type:: annotation
  hl-page:: 6
  hl-color:: green
  id:: 64d9e4b8-b451-4529-9603-ec2fbeb68265
  hl-stamp:: 1692001731778
- Snowflake also performs dynamic pruning during execution
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e4c0-5762-45b3-8d6b-83189063c2b4
- This is in addition to other well-known techniques such as bloom joins 
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e584-60c8-4658-8259-6a6da1b5454a
- Snowflake collects statistics on the distribution of join keys in the build-side records
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e591-1f6c-4084-8d9c-844e5410fb35
- join processing
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e593-fc75-4255-a47b-8424cc921c90
- pushed to the probe side and used to filter and possibly skip entire files on the probe side
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e5a4-163f-4526-89ce-037ab2e8a109
- ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e5be-5630-4370-9cc5-d0ba295ef931
  4. FEATURE HIGHLIGHTS
- comprehensive SQL support
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6a4-dabe-4101-95c2-f2e81a839343
  hl-stamp:: 1692001958784
- ACID transactions
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6aa-4a21-4b59-8d3f-882828bef385
- standard interfaces
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6ac-06a8-4a64-954d-a53099e94a18
- a number of other valuable features rarely or never-before seen in related system
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 64d9e6c0-d050-44a9-a2dc-f635fd32e808
  hl-stamp:: 1692001986559
- 4.1 Pure Software-as-a-Service Experience
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6c9-f78c-4060-af74-e19c55dac7e1
  hl-stamp:: 1692001995629
- Snowflake supports standard database interfaces (JDBC, ODBC, Python PEP-0249) and works with various thirdparty tools and services such as Tableau, Informatica, or Looker
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6e8-d2ed-45d3-b918-2eeffb9c3ef3
- provides the possibility to interact with the system using nothing but a web browser.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6f0-0af3-4f56-b25d-dca483303ff9
- dramatically reducing the complexity of bootstrapping and using the system
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e6ff-498f-4828-8348-1801e35b6795
- , the UI allows not only SQL operations, but also gives access to the database catalog, user and system management, monitoring, usage information, and so forth
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e70f-6c43-4b2a-9c48-43eb75fd765c
- 4.2 Continuous Availability
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e850-103f-4078-abff-c76cac6c47aa
- But as data analysis became critical to more and more business tasks, continuous availability became an important requirement for any data warehouse
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e86f-f419-48f5-8286-343bf4b7be06
  hl-stamp:: 1692002417740
- The two main technical features in this regard are fault resilience and online upgrades.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e8b2-92c5-46c0-8f34-16a38792a665
- Snowflake tolerates individual and correlated node failures at all levels of the architecture
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e8be-30aa-4697-adc3-a31ec3f385df
- [:span]
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e8d6-a273-4425-a7e7-6435c0258c0f
  hl-type:: area
  hl-stamp:: 1692002517546
- Replication across AZs allows S3 to handle full AZ failures, and to guarantee 99.99% data availability and 99.999999999% durability.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e8f5-bb3c-49a2-9d44-1defe6c356d4
- The remaining services of the Cloud Services layer consist of stateless nodes in multiple AZs, with a load balancer distributing user requests between them
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e90a-059e-474e-ae02-89592f66d05c
- possibly some failed queries for users currently connected to a failed node. These users will be redirected to a different node for their next query.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e926-19ce-41dc-99e6-72fbe7e2301c
- Virtual Warehouses (VWs) are not distributed across AZs.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 64d9e92f-1186-4f17-b6cf-cf7baedd0fa5
- High network throughput is critical for distributed query execution, and network throughput is significantly higher within the same AZ
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e944-6acb-4dc0-b977-1d4dd23a0962
- If one of the worker nodes fails during query execution, the query fails but is transparently re-executed, either with the node immediately replaced, or with a temporarily reduced number of nodes
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e954-f316-4557-9a93-0c52366b6e29
- Snowflake maintains a small pool of standby nodes.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e998-d671-48c4-bbe1-2985f6df66a6
- used for fast VW provisioning.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e99d-9ef6-467d-8d78-e438fdfc7c31
- If an entire AZ becomes unavailable though, all queries running on a given VW of that AZ will fail,
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e9ba-e03e-417a-ba49-01c3bfab2c45
- If an entire AZ becomes unavailable though, all queries running on a given VW of that AZ will fail,
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 64d9e9bc-5877-4357-8426-862c57dea0ce
- he user needs to actively re-provision the VW in a different AZ
  ls-type:: annotation
  hl-page:: 6
  hl-color:: red
  id:: 64d9e9c1-0aa7-4144-b902-b8152303d138
- 4.2.2 Online Upgrade
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e9e4-c17e-45be-962a-987b6cddf024
- [:span]
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e9f4-12cb-48d0-8a16-4edb6ea67dc2
  hl-type:: area
  hl-stamp:: 1692002506680
- 4.2.2 Online Upgrade
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9e9fc-8f65-46e7-87e4-4286cf99ae87
- [:span]
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea01-37b8-48d5-8df0-a77fa3610ccd
  hl-type:: area
  hl-stamp:: 1692002511827
- If an entire AZ becomes unavailable though, all queries running on a given VW of that AZ will fail, and the user needs to actively re-provision the VW in a different AZ
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea49-e095-4430-a18b-634fc06b4353
- provides continuous availability not only when failures occur, but also during software upgrades
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea5d-5f1c-4f43-bd73-d8c9d6603d81
- allow multiple versions of the various services to be deployed side-by-side
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea64-e676-4a6c-85e6-1f1764ccff16
- both Cloud Services components and virtual warehouses.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea6a-9e00-45d9-bdfb-32eb9147b60b
- This is made possible by the fact that all services are effectively stateless
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea71-54c9-425f-830a-65d398301609
- All hard state is kept in a transactional key-value store and is ac-
  ls-type:: annotation
  hl-page:: 6
  hl-color:: yellow
  id:: 64d9ea82-9b2f-476b-b59d-65486252804a
- [:span]
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ea88-4400-47a0-a1f4-1bd54839a2b5
  hl-type:: area
  hl-stamp:: 1692002952333
- cessed through a mapping layer which takes care of metadata versioning and schema evolution
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ea94-274e-4a32-afee-196de946331c
- Whenever we change the metadata schema, we ensure backward compatibility with the previous version
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ea9c-2544-49fb-b037-0702bba5422f
- first deploys the new version of the service alongside the previous version.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9eaa7-3231-4fca-8331-6a4e6b6072dc
- User accounts are then progressively switched to the new version, at every which point all new queries issued by the respective user are directed to the new versio
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9eb5b-9ead-4759-8361-433164a54190
- All queries that were executing against the previous version are allowed to run to completion
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9eb6a-e6bc-4401-917b-668ae5fad713
- As mentioned previously, both versions of Cloud Services share the same metadata stor
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9eba3-a7f6-4b21-86de-6d270aa3215c
- VWs of different versions are able to share the same worker nodes and their respective caches
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ebaa-1ee9-4c9d-a004-a8f2d279ce2f
- there is no need to repopulate the caches after an upgrade
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 64d9ebb1-826f-4938-bd6f-ce5d450b9e0b
  hl-stamp:: 1692003262025
- The entire process is transparent to the user with no downtime or performance degradation
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 64d9ebc4-94ee-48c3-bd9f-93f06e6c5622
- At the time of writing, we upgrade all services once per week
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ebe6-6447-4030-8119-942c99534960
- both upgrade and downgrade are continuously tested in a special pre-production incarnation of Snowflake
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ec97-5b47-437f-9001-2158f573257d
- 4.3 Semi-Structured and Schema-Less Data
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 64d9ecb2-8507-44e2-9523-3404847922e3
- extends the standard SQL type system with three types for semi-structured data
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecba-7ef5-4f0b-a44b-7b993484d5b7
- VARIANT
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecbd-3e50-4213-97d4-720703b30b7d
- ARRAY
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecc0-5b56-4b12-967a-f57bc5286789
- OBJECT
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecc2-6b09-45c1-a87d-c6f6390b2ce0
- can store any value of native SQL type (DATE, VARCHAR etc.)
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecc9-e2a7-4c05-a6ce-26451214636f
- as well as variable-length ARRAYs of values
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecd5-a814-48eb-9d3f-de7b545122bb
- JavaScript-like OBJECTs, maps from strings to VARIANT values
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ece6-a1be-498f-a73e-dbceecdbbc29
- also called documents in the literature,
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecef-af96-4286-9647-94cfd212989f
- ARRAY and OBJECT are just restrictions of type VARIANT
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ecf6-5063-4e1c-9126-191d9d8b31d8
- a self-describing, compact binary serialization which supports fast key-value lookup,
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ed02-223d-4d0d-8c62-16d83452d648
- efficient type tests, comparison, and hashing
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ed17-973d-4952-91bf-497189e100ea
- can thus be used as join keys, grouping keys, and ordering keys, just like any other column
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ed1e-1ed4-43b5-a100-a9c12e15b45f
- Users can load their input data from JSON, Avro, or XML format directly into a VARIANT column;
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ed4a-4a2e-4ddc-8c27-0bb4f4d824ec
- Snowflake handles parsing and type inference
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 64d9ed55-fe1a-4db8-8fd0-1f31db1e3a45
  hl-stamp:: 1692003714755
- no need to specify document schemas or to perform transformations on the load
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ed64-8e19-4510-8032-d0b4f168d4c0
- used in an ELT(Extract-Load-Transform) manner rather than a traditional ETL (Extract-Transform-Load) manner
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 64d9ed7c-ac2c-4ff2-9b9b-d7573ab18f56
- aptly called “schema later” in the literature, allows for schema evolution by decoupling information producers from information consumers and any intermediaries.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ed94-d414-4d5f-9aeb-13ead04ef626
- Another advantage of ELT
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9edc6-e8a9-422a-9e70-e2ae389c05a2
- if transformation is desired, it can be performed using the full power of a parallel SQL database, including operations such as joins, sorting, aggregation, complex predicates and so forth
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9edd5-f844-4ec7-9bcc-dcb83abaa76d
- which are typically missing or inefficient in conventional ETL toolchains
  ls-type:: annotation
  hl-page:: 7
  hl-color:: red
  id:: 64d9eddc-4025-4634-8cd7-d4fd8ce3ac01
  hl-stamp:: 1692003808401
- nowflake also features procedural user-defined functions (UDFs) with full JavaScript syntax and integration with the VARIANT data type
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9edfe-0139-42c2-952f-00d499f10a7a
- most important operation on documents is extraction of data elements, either by field name (for OBJECTs), or by offset (for ARRAYs)
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ee3a-994e-433e-a000-95d07cfeab88
- provides extraction operations in both functional SQL notation and JavaScript-like path syntax
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ee40-ee0f-40a9-bd87-f7a2f98b33c0
- A child element is just a pointer inside the parent element; no copying is required
  ls-type:: annotation
  hl-page:: 7
  hl-color:: green
  id:: 64d9ee56-2fda-4a2e-bd44-cff574c95aaf
- The second common operation is flattening
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ee7a-40e4-41e5-94ca-c6bae634d8b9
- pivoting a nested document into multiple rows. 
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9ee80-c04d-4ef2-a01a-7dbd5c85cd70
- ses SQL lateral views to represent flattening operations
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9efd9-4c58-4a1d-abfb-c54ff14872f9
- can be recursive, allowing the complete conversion of the hierarchical structure of the document into a relational table amenable to SQL processing
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9efe1-0d1e-4085-9c78-29279ac9e168
- Snowflake introduces a few new aggregate and analytic functions such as ARRAY_AGG and OBJECT_AGG for this purpose
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9effb-7131-4706-b006-6f37f6e5204d
- 4.3.2 Columnar Storage and Processing
  ls-type:: annotation
  hl-page:: 7
  hl-color:: yellow
  id:: 64d9efff-5559-4668-b8c8-a035511a7583
- which is the usual reason for transforming semi-structured data into plain relational data
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f0e7-6dd7-4b04-8518-77d9a7086d90
- Cloudera Impala [21] (using Parquet [10]) and Google Dremel [34] have demonstrated that columnar storage of semi-structured data is possible and beneficial
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f109-47c6-492c-9126-0c7a5dd3991b
- However, Impala and Dremel (and its externalization BigQuery [44]) require users to provide complete table schemas for columnar storage
  ls-type:: annotation
  hl-page:: 8
  hl-color:: red
  id:: 64d9f119-965f-42e6-afad-da0b63431fb8
  hl-stamp:: 1692004646631
- To achieve both the flexibility of a schema-less serialized representation and the performance of a columnar relational database, Snowflake introduces a novel automated approach to type inference and columnar storage.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: blue
  id:: 64d9f124-0990-492d-b6b6-daace0a2d961
- Snowflake stores data in a hybrid columnar format.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f134-2403-44c3-ac32-8d725a3bedde
- the system automatically performs statistical analysis of the collection of documents within a single table file
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f17c-dd78-453b-bea5-b6a615347072
- automatic type inference and to determine which(typed) paths are frequently common.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f18b-c58e-412c-9384-a4b1aa8caa6c
- The corresponding columns are then removed from the documents and stored separately, using the same compressed columnar format as native relational data
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f1ac-10fa-4b3d-9d8b-b1e9ddf6afbb
- even computes materialized aggregates for use by pruning (cf. Section 3.3.3), as with plain relational data
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f1b1-774f-4004-bbe5-1574419d5fd3
- Most queries, however, are only interested in a subset of the columns of the original document
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f1c1-84ba-4920-a45e-cc07e8f12ed3
- he various columns can be reassembled into a single column of type VARIANT
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f208-4346-44cd-8104-aab7f1c30411
- Snowflake pushes projection and cast expressions down into the scan operator, so that only the necessary columns are accessed and cas
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f217-7277-4b7e-ac80-880283375603
- optimizations described above are performed independently for every table file
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f22b-a431-4c76-9d95-285598e95aaf
- allows for efficient storage and extraction even under schema evolution.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f2ee-8930-4a77-919f-1e646b589abe
- The conservative solution is to simply scan all files for which there is no suitable metadata
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f38f-42fe-4281-85b3-086ba57a99ea
- improves over this solution by computing Bloom filters over all paths
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f39a-b790-412a-b645-ac5d88d82ba7
- Bloom filters are saved along with the other file metadata, and probed by the query optimizer during pruning
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f3a2-b5ae-4907-9a64-500702c05c1d
- Table files which do not contain paths required by a given query can safely be skipped.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f451-eee2-4e5c-a18c-507486d4e541
- 4.3.3 Optimistic Conversion
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f54f-8d0d-4f0c-b42f-23b8e03d6898
- , notably date/time values, are represented as strings in common external formats such as JSON or XML, these values need to be converted from strings to their actual type either at write time (during insert or update) or at read time (during queries).
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f565-0ebb-4594-ab4a-48d29f54a597
- applied at write time, automatic conversions may lose information
  ls-type:: annotation
  hl-page:: 8
  hl-color:: red
  id:: 64d9f587-4614-4992-8a2a-7317fcd55a37
- these string conversions need to be performed at read time, which, in a readdominated workload, is less efficient than doing the conversions once, during the write
  ls-type:: annotation
  hl-page:: 8
  hl-color:: red
  id:: 64d9f593-385e-499d-a06b-4cb8086e989e
- Snowflake solves the problem by performing optimistic data conversion, and preserving both the result of the conversion and the original string 
  ls-type:: annotation
  hl-page:: 8
  hl-color:: blue
  id:: 64d9f5ae-8e12-4218-a302-1cdfeae195ad
- unless a fully reversible conversion exists),
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f5c4-0414-4f67-93ad-989a071aa97a
- in separate columns
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f5c9-ee4a-44c3-b721-63f411e98fcd
- If a query later requires the original string, it is easily retrieved or reconstructed
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f5d3-ef61-4839-ab71-e1db0971c56d
- 4.3.4 Performance
  ls-type:: annotation
  hl-page:: 8
  hl-color:: yellow
  id:: 64d9f5e4-8ff2-4a77-b5ea-a81e0a85d26d
- the overhead of schema-less storage and query processing was around 10% for all but two queries
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f61a-06ff-422c-9ea8-d5e8e9197cb9
- 4.4 Time Travel and Cloning
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f674-c102-4e41-8cc6-95edcaf9ba6e
- SELECT * FROM my_table AT(TIMESTAMP =>’Mon, 01 May 2015 16:20:00 -0700’::timestamp);
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f67d-a9d0-4cf8-b69b-85ada92dfb83
- One can even access different versions of the same table in a single query.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f696-8b71-464c-9b6c-c27e495733dc
- DROP DATABASE important_db; -- whoops! UNDROP DATABASE important_db;
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f6b2-4b0f-4595-a081-7dcd4317fbc1
- Cloning a table creates a new table with the same definition and contents quickly and without making physical copies of table
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f6cb-6628-420f-b37c-6a4d75509739
- The clone operation simply copies the metadata of the source table.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f6d6-0f2c-4fd4-b55e-11aa85c19edd
- but both tables can be modified independently thereafter. 
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f6e1-a6d1-44fd-8ebd-6e4cb5bfcac6
- The CLONE keyword can even be combined with AT and BEFORE, allowing such snapshots to be made after the fact.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: yellow
  id:: 64d9f73d-3d39-4d64-9033-1b909d070b0f
- ls-type:: annotation
  hl-page:: 10
  hl-color:: yellow
  id:: 64d9f7ac-fe7c-468d-bc13-be91241b1959
  5. RELATED WORK
- Cloud-based Parallel Database Systems
  ls-type:: annotation
  hl-page:: 10
  hl-color:: yellow
  id:: 64d9f7af-591c-4c14-9311-306d9bc7ca4f
- Amazon has a number of DBaaS products with Amazon Redshift being the data warehousing product among these. Having evolved from the parallel database system ParAccel, Redshift was arguably the first real data warehouse system offered as a service
  ls-type:: annotation
  hl-page:: 10
  hl-color:: yellow
  id:: 64d9f7b8-e3cf-4fe0-8906-5a7bafbafc6b
- One of the inspirations for Snowflake was BigQuery’s support for JSON and nested data, which we find necessary for a modern analytics platform
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f7f3-153f-4fbc-b903-82f0ce0e980a
- while BigQuery offers a SQL-like language, it has some fundamental deviations from the ANSI SQL syntax and semantics, making it tricky to use with SQL-based products
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f7fa-1b91-4203-bb18-bcf6d0e0026d
- BigQuery tables are append-only and require schemas.
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f801-aca9-41d9-bf8d-5b0c32f34828
- Snowflake offers full DML(insert, update, delete, merge), ACID transactions, and does not require schema definitions for semi-structured data
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f808-bdc0-48aa-b1ac-20042ab50a42
- Computational resources can be scaled through data warehouse units (DWUs). The degree of concurrency is capped though
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f837-5619-4dcb-9fa4-82b26cda4d67
- maximum number of concurrently executing queries is32
  ls-type:: annotation
  hl-page:: 11
  hl-color:: red
  id:: 64d9f83d-5f61-4f9d-a5e6-93f20d0d3ad4
  hl-stamp:: 1692006464167
- it does not have built-in support for semi-structured data comparable to Snowflake’s VARIANT type and related optimizations.
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f854-e12d-44f2-a6ca-18f5369094a0
- However, one challenge that has resulted from the simple keyvalue and CRUD (create, read, update, and delete) API of these systems is the difficulty to express more complex queries.
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f86b-0b0e-4f87-af24-083cba7b3376
- As a result, today, Snowflake has only one tuning parameter: how much performance the user wants (and is willing to pay for).
  ls-type:: annotation
  hl-page:: 11
  hl-color:: blue
  id:: 64d9f8ce-d6d6-4e9e-a4b9-a47d1a30d315
- Building a metadata layer that can support hundreds of users concurrently was a very challenging and complex task
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f8dc-5914-4f57-bd7c-5ef7b56e8b20
- Security has been and will continue to be a big topic: protecting the system and the users’ data from external attacks, the users themselves, and our internal users as well
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f8e5-739d-4ce8-930d-778f20c2b5c6
- Maintaining a live system of hundreds of nodes running millions of queries per day, while bringing a lot of satisfaction, requires a highly integrated approach to development, operations, and support.
  ls-type:: annotation
  hl-page:: 11
  hl-color:: yellow
  id:: 64d9f8e9-9105-45ba-af04-748cf76f32a5