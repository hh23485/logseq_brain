tags:: [[Computer Science - Distributed]], [[Parallel]], [[and Cluster Computing]]
date:: [[Jan 31st, 2022]]
issn:: "0360-0300, 1557-7341"
issue:: 10s
extra:: arXiv:2112.12921 [cs]
doi:: 10.1145/3508360
title:: The Serverless Computing Survey: A Technical Primer for Design Architecture@Paper
pages:: 1-34
volume:: 54
item-type:: [[journalArticle]]
access-date:: 2022-11-28T02:30:10Z
original-title:: The Serverless Computing Survey: A Technical Primer for Design Architecture
language:: en
url:: http://arxiv.org/abs/2112.12921
short-title:: The Serverless Computing Survey
publication-title:: ACM Computing Surveys
journal-abbreviation:: ACM Comput. Surv.
authors:: [[Zijun Li]], [[Linsong Guo]], [[Jiagan Cheng]], [[Quan Chen]], [[Bingsheng He]], [[Minyi Guo]]
library-catalog:: arXiv.org
links:: [Local library](zotero://select/library/items/C99HVFHM), [Web library](https://www.zotero.org/users/10443130/items/C99HVFHM)

- [[Abstract]]
	- ((638c283c-b8e5-4f9a-8995-f4be5ea35a67))
	- ((638c2879-c61c-4d1d-90e0-de52d9031cf4))
		- ((638c2882-bd29-447a-9bc8-4e0ed38b6dc4))
	- ((638c28a1-c9fc-4df4-9536-399280a124eb))
		- ((638c28c6-35ad-4828-a907-1f8fe7a9cfd5))
- [[Attachments]]
	- ![The Serverless Computing Survey A Technical Primer for Design Architecture.pdf](../assets/The_Serverless_Computing_Survey_A_Technical_Primer_for_Design_Architecture_1670129409560_0.pdf)
- [[Notes]]
	- # Introduction
	  collapsed:: true
		- ## Definition of Serverless Computing
		  collapsed:: true
			- ((638c2a2b-b430-4989-abbe-aaca559d4ae3))
				- ((638c2a40-eb22-4da3-926b-5e1af65859c5))
					- ((638c2a4f-0910-4b4b-ab2d-0972be6f2d12))
					- diurnal: 昼夜的，流量如果呈现出昼夜的不同的 pattern，或者分时不同的流量，就意味着需要预留足够的资源，也导致资源不能够充足的被利用
				- ((638c2af0-1d21-4a4f-8288-19121e121cba))
					- ((638c2b0c-9963-4d6c-bae9-10c5d94fb85c))
					- ((638c2b1b-378d-4c1b-9bf7-5c1fce695a7f))
				- ((638c2b70-2ef8-47eb-8d1c-29759c526155))
			- ### ((638c2c5b-d23f-4947-8f73-60504e99a251))
				- #### Common definitions
				  id:: 638c2bf8-1824-430c-b5c1-dd0432f81303
					- ((638c2cbf-a800-44c1-9921-b2e3213a1deb))
						- ((638c2ce9-06fe-4ff5-9d3f-297a8bdd4412))
						- ((638c2d00-17f6-4bc2-a726-5169857097e6))
						- ((638c2d05-2ac3-45d6-8be9-dd180edd3299))
					- ((638c2d69-8b82-4ecb-a639-38df62914be2))
					- ((638c2da0-d898-4203-ab2b-4c805b07c381))
						- A few services relies on like cloud storage, message bus sytem, DevOps tools
				- #### Computing model
					- ((638c2f99-bd82-45a6-bca4-dd60f740d073))
					- ((638c3007-8f76-4289-ba29-901ec44b8015))
						- ((638c3017-dd38-4963-b60e-5ea3701a13e5))
						- ((638c301e-7c08-4a3e-b1f6-b0a5618d0c42))
					- ((638c303a-ecf0-465a-ae17-25ecfe7ba5a4))
					- ((638c3097-abb9-4f42-9c41-1f335e142faa))
						- ((638c30dd-b6f1-4fa4-8748-17427486279b))
						- ((638c30f7-f20a-4d13-8178-e21507095ab4))
				- #### Five features
					- ((638c33b0-dd96-484e-9580-5431b88ad4a8))
						- ((638c3434-36c2-49f4-9ca1-3985389f8a11))
					- ((638c33b8-b95f-4439-9a33-ebf4369c9e0a))
						- ((638c3466-3ecc-49d4-a369-1e338fa9354c))
						- ((638c4e2c-c2f1-420f-ba9e-7e7e10da0eec))
							- ((638c4e51-b62a-4093-9b0b-a4a1d210adf4))
					- ((638c33be-7271-49e9-a464-e82bd690f7e8))
						- ((638c76d0-ff03-4612-8b39-48f3c33bd64a))
							- ((638c76dd-39c9-485e-91da-a42d337c97ac))
							- ((638c7717-9008-4bbd-852f-cebe7472d3f3)). ((638c7732-ed4a-4cad-937c-45affd683ec3))
								- ((638c7764-a45d-4602-a7ce-ec2c8fe7a41c))
					- ((638c33c4-8870-4187-baf1-bd101d7e9ac8))
						- ((638c77ed-47a9-4d17-ba79-49538b081f10))
						- ((638c7816-b8ad-45f7-98b2-892569b81d7c))
					- ((638c33cb-5c6c-4a90-870c-931ace8d1357))
						- ((638c7827-cba9-4c3f-9459-852a8eb88259))
							- ((638c7841-45d5-4ea0-8eff-2b3288b50c14))
				- #### Scenario
					- ((638c78b2-48b0-498c-89b7-d99418eff88d))
		- ## Survey Method by the Layered Serverless Architecture
		  collapsed:: true
			- 很难把握和真正理解架构中的每个问题
			- ((6395fb78-d0e2-46ee-a616-974ab84cda2f))
				- ((6395fb85-cd3a-49bd-8658-759d12406545))
				- ((638cb398-2b8c-48a5-8ed3-2e4f0faa91ec))
			- 图中自底向上分成了 4 层
				- ### ((63a90973-a4b2-4d69-8a0e-181030aef848))
					- ((63a9097d-2096-4c62-a974-ad92b7923549))
					- ((63a90996-ebdd-442a-a788-e4c3495ddf8d))
					- ((63a909aa-7044-49b4-9002-bb49c20141f6))
					- ((63a909b4-6ad4-4a28-b7c7-8a0d41d361e6))
				- ### ((63b2fcc4-fbd9-46ea-8744-1f4fa6fca58a))
					- ((63b2fd47-2a8d-4b6c-945e-0a034236474f))
					- ((63b2fd80-a930-4163-9804-f41a1ce03df6))
						- ((63b2fd92-6428-4fbf-80f4-3bf9ef53e7b1))
					- ((63b2fde1-7a83-474a-90b6-dd5401efb5ac))
						- ((63b2fdb7-a478-4c0a-b2c1-910850298ec5))
						- ((63b2fdf0-a8dc-4173-acc5-e8e1ef5db9ac))
						- ((63b2fdf8-8a74-4206-bd1d-a927f6e23d4f))
				- ### ((63b2fe0d-e025-4f43-b37a-5acd4ac734c0))
					- ((63b2fe58-082b-48c3-a7e9-e9ebbf06cb25))
					- ((63b2fe63-2fe2-4e5e-b1dd-57ad991f9aa7))
						- ((63b2fea7-f922-4c94-b3c4-097bcec889a9))
						  tags:: 不懂
						- ((63b2fefa-ed04-4234-9bc2-2f03794d307c))
							- ((63b2ff17-3c80-417d-991a-a93b162b34c5))
								- ((63b2ff27-3e78-47a8-aa6b-fa7425b934fe))
								- ((63b2ff31-8da6-4ca3-8a91-cb22ea0382c4))
								- ((63b2ff38-359b-4094-ad30-8583911ad2a9))
				- ### ((63b2ff4d-2305-48ea-8ed9-eb4b4f9db5d0))
					- ((63b2ffb5-e46e-4c21-88a9-5cc58c020b1b))
						- ((63b2ffe2-9e1e-45d1-ad30-95cb448091ca))
						- ((63b2fffa-b6ca-476c-93af-b8f9ff18374c))
	- # Virtualization Layer
	  collapsed:: true
		- ((63b44e28-a2d7-49ab-9f6d-8e4a12aba803))
		- ((63b44e50-0f48-4715-b202-24a91d7e136b))
		- ((63b44e83-c471-49b4-b335-5d8467a50064))
			- ((63b44ea0-fbb6-42bf-a4c6-f971f2a9b424))
			- ((63b44eac-b5de-4b19-8a9f-66e5f194a684))
			- ((63b44eb8-3c0d-4c25-8caa-634b3efc77e2))
		- 沙盒技术
			- ((63b44f38-eb11-48d7-a358-768867ca1570))
			- ((63b44f41-828a-49ec-957a-9ed4a6ee3da6))
			- ((63b44f48-3f10-4543-aa9f-526b11cc6bf0))
			- ((63b44f4d-04a5-4642-bcbf-39462ec691bc))
			- 对比
				- Summary ((63bcb80f-53d8-4720-b605-59bf86249633))
					- Startup latency: ((63c36535-ef11-43fe-a231-2773cbe338b3))
					- Isolation level: ((63c3654b-64bb-4d23-827d-362f09e7be84))，不受他人干扰运行的能力
					- OSKernel: ((63c36582-2ee3-47f8-ab9f-af8d98bbb4dd))
					- Hotplug: ((63ce02eb-5dc9-4bcc-af80-1af703b53b04))
					- OCI supported: ((63ce0309-268d-46e3-906b-ce46d2f124aa))
				- 传统基于 VM 的隔离
				  collapsed:: true
					- 特点
						- ((63ce1aa2-5fab-4cdb-befc-608dd31faec0))
							- like hypervisor
						- ((63ce1af2-36f3-47db-be21-01261dca4a97))
						- ((63ce1b12-929d-4eab-beaa-1675587969ff))
					- 优点
						- ((63ce1b24-37b7-4261-aa82-d52f384fb96f))
					- 缺点
						- ((63ce1b37-5a25-4e4f-be27-180b443b16c4))
							- ((63ce1b76-31ae-417f-846c-8e9e18d7978b))
				- 容器
				  collapsed:: true
					- 特点
						- ((63ce1c90-3034-44be-9341-3c25225ff81d)).
						- ((63ce1ca3-5672-4deb-80ea-93cdae538498))
							- ((63ce1cc2-daae-4b91-9fd4-3c55ae86afbe))
						- ((63ce1ced-3ab9-4990-94ed-9a0d92c9d077))
						- ((63ce1d15-1ba3-425c-a73a-9bd8c5e91202))
					- 优点
						- ((63ce1d27-b043-4159-98ec-c627127f3027))
					- 实现
						- Docker
							- ((63ce1d92-82ec-4e72-b705-10e8891e9517))
							- ((63ce1e62-6606-4d2f-aba9-82863e82be66))
						- SOCK
							- ((63ce1e7e-f020-419f-bced-6aaf326170bc))
							- ((63ce1eac-2c24-4019-8713-b8df7734a198))
								- ((63ce1f00-b15e-4eb8-94bf-3052f0c55a96))
								- ((63ce1f30-ff66-4713-aef1-da6b9152e9cb))
						- CNTR
							- ((63ce1fd8-9ea8-4670-8b1f-1f50e60f83d0))
							- ((63ce1f7e-3991-421e-829d-58446efbfa52))
								- ((63ce1fa7-4f87-44d7-bbce-9c11a904c87c))
								- ((63ce1fbe-6962-4394-9812-e5a845312218))
					-
				- 安全容器
				  collapsed:: true
					- 安全问题 - 隔离能力不足
						- ((63ce2149-1cfa-4288-ab46-46d56f0932f2))
						- ((63ce2062-a2ea-4787-abc5-f479012ab609))
							- ((63ce20d8-e3ac-4e55-9c3f-70123e608d9c))
							- ((63ce21ae-414d-4338-89e2-cc4e6ac2e758))
					- 实现
						- ((63ce21ec-88b8-44f9-9068-06121a78a193))
							- ((63ce2204-f574-48eb-9b77-722837a8603e)). ((63ce2230-4760-4595-bc57-757dc2f89d45))
							  collapsed:: true
								- ((63ce2261-63b3-453c-9dc0-c5248b283a84))
								- ((63ce227a-0502-49b0-a1d1-701233bf740d))
							- ((63ce234b-ccb7-4388-b2ba-708762e5980f))
							  collapsed:: true
								- ((63ce22c7-6733-4ebb-a139-83546771a8c9))
								- ((63ce2336-e813-4a45-bf9e-e97add7d0d15))
									- ((63ce2447-c4e2-4a21-a593-d6abbe3f722f))
							- ((63ce2503-56e7-4128-99ea-3ac31919b5af)) #疑问
							  collapsed:: true
								- ((63ce2522-a91c-4144-a3cb-88ce7ce08aa0))
							- ((63ce2555-6c64-4c60-8317-c04b6efee9bc))
							  collapsed:: true
								- ((63ce2574-e459-4af6-b975-395febf46906))
					- 优点
						- ((63ce258c-1db7-4ec2-8615-7b1b15006564))
					- 缺点
						- ((63ce259d-dec4-43ab-be50-22fbb9f6c002))
					- TODO How microVM works?
				- [统一内核](((63ce272e-682e-455d-9c01-d0561d82be47)))
					- 特点
						- ((63ce2777-66e1-44e5-86ad-148f3ee51b1e))
							- ((63ce27a1-b57f-4e97-b4df-7147aa890f29))
							- ((63ce27c1-fda2-4284-952b-c407f421f6f0))
								- ((63ce27e1-0299-40a8-a84d-c94670a888f3))
								- ((63ce27f3-87c3-4d13-b36d-04b05208dc57))
								- ((63ce2803-1726-4caf-86ec-910ee1470778))
					- 实现
						- LightVM
							- ((63ce2882-ff5e-4731-92fd-01f524825d85))
						- HermitTux
							- ((63ce28ba-5dac-42a3-972a-734e2266aba2))
								- ((63ce28ca-4633-4247-9d1f-88d135c2e995))
								- ((63ce28db-d043-4316-8f84-258bef6d959b))
								- ((63ce2dc9-d25f-46e1-a132-b12697da31ba)) #疑问
			- ((63ce2e47-9149-442e-8c63-bb35ecd7ce23))
				- ((63ce2eaf-920b-4fb7-9b55-3d70b4cb3ccd))
					- From this perspective, Secure Container is great for prod, and Container is good for dev
				-
	- # Encapsule Layer
		- ((63ce3210-7c84-4e90-969e-139149ef4554))
			- ((63ce3d22-8a9e-479c-b016-9aac95d0a404))
		- ((63ce4064-41b1-4592-804e-023190c9880a))
		- 产品对比
			- ((63ce407f-e3d2-4efe-98ff-3869a6cf67ca))
				- Template: ((63ce41f0-2f7a-48d5-9f1e-1b51766532a5))
				- Static image: ((63ce41fc-5a15-4717-bd1c-fa85781e3ed8)) #疑问
				- Pool: ((63ce4206-42b4-4b74-87ff-4332d712d84d))
				- Predict/Heuristic: ((63ce4214-89e1-47f6-85ab-cd499f82fb9d))
				- REQa: ((63ce421b-3d71-4696-9840-d6d78499fc28))
				- C/R: ((63ce4221-7373-452c-afe5-097080864d5f))
				- Sidecar: ((63ce4225-cbb6-4627-90e7-46d483a7a832))
				- Imp: ((63ce4228-bce8-439a-b869-df458c180666))
		- Startup approaches
			- ((63ce4dae-34ef-476d-92d7-35d9785e5af1))
			- ((63ce4db8-58bd-478b-968c-f77afd833d61))
		-