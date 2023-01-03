tags:: [[Computer Science - Distributed]], [[Parallel]], [[and Cluster Computing]]
date:: [[Jan 31st, 2022]]
issn:: "0360-0300, 1557-7341"
issue:: 10s
extra:: arXiv:2112.12921 [cs]
doi:: 10.1145/3508360
title:: @The Serverless Computing Survey: A Technical Primer for Design Architecture
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
		- ## ((638c2951-7cef-456b-ac28-2a5be85820a9))
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
		- ((63b44e28-a2d7-49ab-9f6d-8e4a12aba803))
		- ((63b44e50-0f48-4715-b202-24a91d7e136b))
		- ((63b44e83-c471-49b4-b335-5d8467a50064))
			- ((63b44ea0-fbb6-42bf-a4c6-f971f2a9b424))
			- ((63b44eac-b5de-4b19-8a9f-66e5f194a684))
			- ((63b44eb8-3c0d-4c25-8caa-634b3efc77e2))
			-
		-