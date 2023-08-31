tags:: Paper

- ![Building An Elastic Query Engine  on Disaggregated Storage.pdf](../assets/Building_An_Elastic_Query_Engine_on_Disaggregated_Storage_1692007378670_0.pdf)
- TOC {{renderer :tocgen, [[]], 2, h}}
- # Abstract
	- ((64d9fc0c-0400-498b-82b6-218e3b6e114f))
	- ((64d9fc31-5299-48a1-be84-c97ea1fa7b81))
	- ((64d9fc35-eb9b-4e6a-b44b-c1950ca1a9ba))
- # 1. Introduction
	- ((64d9fc82-e198-4f8f-ba35-ea895f8452a6))
	- ((64d9fc84-c84e-49bc-8739-eade7103c623))
		- ((64d9fca7-95d8-48eb-9a90-df734ed98117))
			- ((64d9fcca-30a6-4306-9f3f-787e151dbb71))
			- ((64d9fce4-7ce1-4dfc-bf8f-0d1050e9b1b3))
		- ((64d9fcfc-144a-448a-82f2-f21d28918c95))
			- ((64d9fd4c-9f31-4fa7-8f74-e4ce4ad4a3f7))
			- ((64d9fd59-450b-4172-a23a-719eac852c4b))
				- ((64d9fd66-cf96-42d3-accd-d976936b20c9))
		- ((64d9fdbf-5d9c-46dd-8b5c-875684fe59ae))
			- ((64d9fdcc-166b-4972-809a-7c6787d259c5))
	- For snowflake backgrounds, go to [[The Snowflake Elastic Data Warehouse@Paper]]
- # 2. Design Overview
	- ## 2.1 Persistent and Intermediate data
		- ((64da1152-446c-4834-8b44-4b45ec7c24dc))
			- ((64da1145-f04b-4e91-a146-8ef1a96e4881))
			- ((64da1168-3312-42df-b6a6-1e25601818dc))
				- ((64da1183-0978-4b79-a27a-00ec0d07f4ad))
			- ((64da11d5-085a-4b15-994c-252faaa9f218))
	- ## 2.2 End-to-end System Architecture
		- ((64da1241-da5e-419a-aa06-4ffa204d918e))
			- ((64da1250-b212-40b3-a742-cab379616765))
		- ((64da12a5-f340-4773-baaa-0941a0c1a38f))
			- ((64da12dd-6518-4f04-8c9d-03cdc6f4e6ad))
			- ((64da12f1-2187-4cd4-8c9c-9a422ba854cd))
			- Global, cross region
		- ((64da12b0-99f8-4067-855d-021d07bc4062))
			- ((64da1334-f3e7-4a30-b3e8-2f0531e0d82f))
			- ((64da133f-f41d-4071-826d-b70122922859))
			- ((64da137e-7c1c-41c0-a8b4-95df7eb6445c))
			- ((64da138f-f7de-47b5-8e58-25c2f2213f70))
		- ((64da12b5-0b37-4275-b31e-ebed5444766c))
			- ((64da152b-4a2e-431b-a3e3-21c25221ad02))
			- ((64da151f-24fe-4a73-9d34-ecb4234320f5))
				- ((64da1630-8aa3-467b-9096-7557880da722))
			- ((64da166a-387e-4149-9ee3-4882be91cca3))
		- ((64da12bc-f2c6-49e6-9436-6a6a14b8e099))
			- ((64da16a4-a654-44d5-9b13-e871cff27bb4))
				- ((64da16d6-8f4b-4b8c-95c0-e061b588199f))
			- ((64da16e4-d755-42bf-be28-f4db6a0bc914))
				- ((64da16f3-c6db-4b5b-9958-e1564f21e805))
			- ((64da1707-d846-4b7a-9106-1a0a7af68e66))
				- ((64da1b10-98cb-4136-856e-76a1d6b7d8bc))
				- ((64da1b1a-3068-42f5-9263-16d79bce9bbf))
					- ((64da1b27-07bb-4b67-998a-e47d98a8e930))
	- ## 2.3 End-to-end query execution
		-