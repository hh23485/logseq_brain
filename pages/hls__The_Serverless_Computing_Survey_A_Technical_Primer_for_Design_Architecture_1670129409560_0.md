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
- isolation ensures that each function invocation runs in an individual container or a virtual machine assigned from an access-control controller.
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 638c303a-ecf0-465a-ae17-25ecfe7ba5a4
  hl-stamp:: 1670131775153