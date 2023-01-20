tags:: [[Apache Beam]]

- Here is a sample of how to build a simple Apache Beam pipeline
- # ((6397e544-e63c-49a1-a730-6791974556c2))
	- ((6397eaa1-205e-4660-ac29-3c32abbf9328)), for the data please refer to [code base](((6397e02b-fc43-40f9-ba00-9360dc2e8aec)))
		- ```java
		  ClassLoader loader = FirstPipeline.class.getClassLoader();
		  String file = loader.getResource("lorem.txt").getFile();
		  List<String> lines = Files.readAllLines(Paths.get(file), StandardCharsets.UTF_8);
		  ```
	- ((6397ea84-40d5-4d72-a1a8-cfe88ad88161)), it's the container of task DAG
		- ```java
		  Pipeline pipeline = Pipeline.create();
		  ```
	- ((6397ebed-6626-44ec-9c5f-f5e6215a2367))
		- ((6397ec4d-68ba-4c21-b931-d02bd7fd4a20))
		- So will create with `PTransforms` actions like follows
	- Create first nodes in the pipeline with `PTransforms` and ((6397ecda-2cd0-4705-b997-c695db5f4cb1))
		- ``` java
		  PCollection<String> input = pipeline.apply(Create.of(lines));
		  ```
		- A output can come from one `PTransform`, and could be consumed by multi `PTransform`
		- ((6397ecf1-80f2-449b-9bc1-8ba8540c7092))
		  id:: 6397ecbb-a710-462e-8b71-4b019dc061ec
			- In this graph, ((6397eea7-7682-443f-8963-0490080b6bd6))
	- Apply the output to another `PTransform`
		- ``` java
		  PCollection<String> words = input.apply(Tokenize.of());
		  ```
			- ((6397ef6c-be20-4191-814d-572a4a2a7987))
				- ((6397ef7d-5233-4a66-b6ff-852e68e09d6c))
				- ((6397efa4-fd35-444f-946f-057787890361))
	- Again, add more `PTransforms`
		- ((6397f02d-63fe-4845-ab40-a3ee8f38107a))
		- ((6397f03a-47b8-4cf7-9f2b-fb6e9d1c317a))
		- ``` java
		  PCollection<KV<String, Long>> result = words.apply(Count.perElement());
		  result.apply(PrintElements.of());
		  ```
			- ((6397f0d3-3da7-46d6-be97-b81d8a943b61))
			- ((6397f1ba-ceec-41d3-8f01-3664bdcc1112))
	- To run the pipeline, use this codes
		- ``` java
		  pipeline.run().waitUntilFinish();
		  ```
		- ((6397f13b-4a59-488f-8c0b-abf915ba722a))
			- ((6397f15a-68e8-4593-a28b-7a38971a2c18))
				- only for test
	- Execute with
		- ``` bash
		  ../mvnw exec:java \
		  Dexec.mainClass=com.packtpub.beam.chapter1.FirstPipeline
		  ```
- # Write as a chain
	- ((6397f261-2337-4f5e-bb2e-ecc5ff83a3f6))
		- ``` java
		  // as a chain
		  pipeline.apply(Create.of(lines))
		          .apply(Tokenize.of())
		          .apply(Count.perElement())
		          .apply(PrintElements.of());
		  pipeline.run().waitUntilFinish();
		  ```
		-
