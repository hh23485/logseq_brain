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