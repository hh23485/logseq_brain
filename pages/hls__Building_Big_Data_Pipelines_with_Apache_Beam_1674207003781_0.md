file-path:: ../assets/Building_Big_Data_Pipelines_with_Apache_Beam_1674207003781_0.pdf

- Building Big Data Pipelines with Apache Beam
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
  id:: 6397de8e-1a39-4bde-8732-772f2fb59dd5
- Chapter 1: Introduction to Data Processing with Apache Beam
  ls-type:: annotation
  hl-page:: 42
  hl-color:: yellow
  id:: 6397deef-69d1-4208-8780-17cb514d2d1a
- Mind-blowing applications can be developed from the successful application of (theoretically) simple logic – take data and produce knowledge.
  ls-type:: annotation
  hl-page:: 42
  hl-color:: yellow
  id:: 6397df20-1f30-49a7-870a-54a4c3114bc5
- However, a simple-sounding task can turn out to be difficult when the amount of data needed to produce knowledge is huge (and still growing)
  ls-type:: annotation
  hl-page:: 42
  hl-color:: red
  id:: 6397df2e-36ce-49d9-ac08-ad7392c701b9
- Given the vast volumes of data produced by humanity every day, which tools should we choose to turn our simple logic into scalable solutions?
  ls-type:: annotation
  hl-page:: 42
  hl-color:: yellow
  id:: 6397df4f-acb7-47c8-bece-c753b86f56b7
- Apache Beam might be a good solution to these challenges
  ls-type:: annotation
  hl-page:: 42
  hl-color:: blue
  id:: 6397df87-9f78-40fd-8ebe-9e0e87f901ff
  hl-stamp:: 1670902677365
- Although it is possible to run many tools in this book using the Windows shell, we will focus on using Bash scripting only.
  ls-type:: annotation
  hl-page:: 43
  hl-color:: purple
  id:: 6397e162-7fa7-479a-8d9a-959b7d9871be
  hl-stamp:: 1670898022987
- Why Apache Beam?
  ls-type:: annotation
  hl-page:: 44
  hl-color:: yellow
  id:: 6397e187-693b-40b1-b2a2-88412fc1a86a
- **What problem** am I struggling with that the new technology can help me solve?
  ls-type:: annotation
  hl-page:: 45
  hl-color:: yellow
  id:: 6397e19a-4c06-4f77-9aeb-fcc32c8a7575
- What would the **costs** associated with the technology be?
  ls-type:: annotation
  hl-page:: 45
  hl-color:: yellow
  id:: 6397e19c-647d-48b2-b254-9008c3a94375
- portability
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  id:: 6397e1fd-c0fe-401a-940e-f46b3c4471be
  hl-stamp:: 1670898181587
- Beam's pipelines are portable between multiple runners
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  id:: 6397e20e-a748-4403-b12d-6c8998d60415
  hl-stamp:: 1670898192065
- data processing model is portable between various programming languages
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  id:: 6397e23c-16df-4760-a57b-42dc9dbf9033
- data processing logic is portable between bounded and unbounded data
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  id:: 6397e245-cee7-42fd-bdbc-019cdd806a64
- mean the possibility to run existing pipelines written in one of the supported programming languages (for instance, Java, Python, Go, Scala, or even SQL) against a data processing engine that can be chosen at runtime
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  id:: 6397e27f-f057-4062-b05b-72f48aab17db
- a runner would be Apache Flink, Apache Spark, or Google Cloud Dataflow
  ls-type:: annotation
  hl-page:: 46
  hl-color:: green
  id:: 6397e298-4f4a-418b-8e68-fdecbd4fcde7
- it has the ability to provide support for multiple SDKs, regardless of the language or technology used by the runner.
  ls-type:: annotation
  hl-page:: 46
  hl-color:: green
  id:: 6397e31c-8ee0-4b5f-b112-9a2cc9c732ab
- ==we can code Beam pipelines in the Go language, and then run these against the Apache Flink Runner, written in Java==
  ls-type:: annotation
  hl-page:: 46
  hl-color:: green
  id:: 6397e332-88da-49a2-a634-ec9ba4d69294
- Choose your preferred language, write your data processing pipeline, run this pipeline using a runner of your choice, and do all of this for both batch and real-time data at the same time.
  ls-type:: annotation
  hl-page:: 47
  hl-color:: yellow
  id:: 6397e38a-56d9-4890-b6e7-5d6c0a6583d9
- should expect to pay for flexibility like this – this price would be a somewhat bigger overhead in terms of CPU and/or memory usage.
  ls-type:: annotation
  hl-page:: 47
  hl-color:: red
  id:: 6397e3b1-bb15-4cd4-a067-d54e39a21fa0
- Writing your first pipeline
  ls-type:: annotation
  hl-page:: 47
  hl-color:: yellow
  id:: 6397e423-b087-42c3-a1d9-d35e59fa40c8
- most important parts here
  ls-type:: annotation
  hl-page:: 47
  hl-color:: yellow
  id:: 6397e544-e63c-49a1-a730-6791974556c2
- create a Pipeline object
  ls-type:: annotation
  hl-page:: 48
  hl-color:: yellow
  id:: 6397ea84-40d5-4d72-a1a8-cfe88ad88161
- read this input from the resource called lorem.txt
  ls-type:: annotation
  hl-page:: 48
  hl-color:: yellow
  id:: 6397eaa1-205e-4660-ac29-3c32abbf9328
- start filling it with data
  ls-type:: annotation
  hl-page:: 48
  hl-color:: yellow
  id:: 6397ebed-6626-44ec-9c5f-f5e6215a2367
- Each `PCollection` object (that is, parallel collection) can be imagined as a line (an edge) connecting two vertices(`PTransforms`, or parallel transforms) in the pipeline's DAG
  hl-stamp:: 1670900814730
  hl-page:: 48
  ls-type:: annotation
  id:: 6397ec4d-68ba-4c21-b931-d02bd7fd4a20
  hl-color:: green
- takes raw input from the list and creates a new PCollection
  ls-type:: annotation
  hl-page:: 49
  hl-color:: yellow
  id:: 6397ecda-2cd0-4705-b997-c695db5f4cb1
- [:span]
  ls-type:: annotation
  hl-page:: 49
  hl-color:: yellow
  id:: 6397ecf1-80f2-449b-9bc1-8ba8540c7092
  hl-type:: area
  hl-stamp:: 1670900975910
- main output(PCollection of PTransform, called Create) is not presently consumed by any PTransform
  ls-type:: annotation
  hl-page:: 49
  hl-color:: yellow
  id:: 6397eea7-7682-443f-8963-0490080b6bd6
- This creates a new PTransform (Tokenize) and connects it to our input PCollection
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
  id:: 6397ef6c-be20-4191-814d-572a4a2a7987
- [:span]
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
  id:: 6397ef7d-5233-4a66-b6ff-852e68e09d6c
  hl-type:: area
  hl-stamp:: 1670901628516
- Tokenize `PTransform` **takes input lines of text and splits each line into words**, which **produces a new `PCollection` that contains all of the words** from all the lines of the input `PCollection`
  hl-page:: 50
  ls-type:: annotation
  id:: 6397efa4-fd35-444f-946f-057787890361
  hl-color:: yellow
- produce the well-known word count example
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
  id:: 6397f02d-63fe-4845-ab40-a3ee8f38107a
- simply print the output PCollection to standard output
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
  id:: 6397f03a-47b8-4cf7-9f2b-fb6e9d1c317a
- [:span]
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  id:: 6397f0d3-3da7-46d6-be97-b81d8a943b61
  hl-type:: area
  hl-stamp:: 1670901970099
- This causes the pipeline to be passed to a runner (configured in the pipeline
  ls-type:: annotation
  hl-page:: 51
  hl-color:: green
  id:: 6397f13b-4a59-488f-8c0b-abf915ba722a
  hl-stamp:: 1670902077557
- The standard default runner is the DirectRunner, which executes the pipeline in the local Java Virtual Machine (JVM) only
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  id:: 6397f15a-68e8-4593-a28b-7a38971a2c18
- The ordering of output is not defined and is likely to vary over multiple runs. This is to be expected and is due to the fact that the pipeline underneath is executed in multiple threads.
  ls-type:: annotation
  hl-page:: 52
  hl-color:: yellow
  id:: 6397f1ba-ceec-41d3-8f01-3664bdcc1112
- simplified to the following:
  ls-type:: annotation
  hl-page:: 52
  hl-color:: yellow
  id:: 6397f261-2337-4f5e-bb2e-ecc5ff83a3f6