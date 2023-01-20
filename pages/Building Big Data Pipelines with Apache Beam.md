file:: [Building_Big_Data_Pipelines_with_Apache_Beam_1674207003781_0.pdf](../assets/Building_Big_Data_Pipelines_with_Apache_Beam_1674207003781_0.pdf)
file-path:: ../assets/Building_Big_Data_Pipelines_with_Apache_Beam_1674207003781_0.pdf

- Building Big Data Pipelines with Apache Beam
  ls-type:: annotation
  hl-page:: 2
  hl-color:: yellow
- Chapter 1: Introduction to Data Processing with Apache Beam
  ls-type:: annotation
  hl-page:: 42
  hl-color:: yellow
- Mind-blowing applications can be developed from the successful application of (theoretically) simple logic – take data and produce knowledge.
  ls-type:: annotation
  hl-page:: 42
  hl-color:: yellow
- However, a simple-sounding task can turn out to be difficult when the amount of data needed to produce knowledge is huge (and still growing)
  ls-type:: annotation
  hl-page:: 42
  hl-color:: red
- Given the vast volumes of data produced by humanity every day, which tools should we choose to turn our simple logic into scalable solutions?
  ls-type:: annotation
  hl-page:: 42
  hl-color:: yellow
- Apache Beam might be a good solution to these challenges
  ls-type:: annotation
  hl-page:: 42
  hl-color:: blue
  hl-stamp:: 1670902677365
- Although it is possible to run many tools in this book using the Windows shell, we will focus on using Bash scripting only.
  ls-type:: annotation
  hl-page:: 43
  hl-color:: purple
  hl-stamp:: 1670898022987
- Why Apache Beam?
  ls-type:: annotation
  hl-page:: 44
  hl-color:: yellow
- **What problem** am I struggling with that the new technology can help me solve?
  ls-type:: annotation
  hl-page:: 45
  hl-color:: yellow
- What would the **costs** associated with the technology be?
  ls-type:: annotation
  hl-page:: 45
  hl-color:: yellow
- portability
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  hl-stamp:: 1670898181587
- Beam's pipelines are portable between multiple runners
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
  hl-stamp:: 1670898192065
- data processing model is portable between various programming languages
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
- data processing logic is portable between bounded and unbounded data
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
- mean the possibility to run existing pipelines written in one of the supported programming languages (for instance, Java, Python, Go, Scala, or even SQL) against a data processing engine that can be chosen at runtime
  ls-type:: annotation
  hl-page:: 45
  hl-color:: green
- a runner would be Apache Flink, Apache Spark, or Google Cloud Dataflow
  ls-type:: annotation
  hl-page:: 46
  hl-color:: green
- it has the ability to provide support for multiple SDKs, regardless of the language or technology used by the runner.
  ls-type:: annotation
  hl-page:: 46
  hl-color:: green
- ==we can code Beam pipelines in the Go language, and then run these against the Apache Flink Runner, written in Java==
  ls-type:: annotation
  hl-page:: 46
  hl-color:: green
- Choose your preferred language, write your data processing pipeline, run this pipeline using a runner of your choice, and do all of this for both batch and real-time data at the same time.
  ls-type:: annotation
  hl-page:: 47
  hl-color:: yellow
- should expect to pay for flexibility like this – this price would be a somewhat bigger overhead in terms of CPU and/or memory usage.
  ls-type:: annotation
  hl-page:: 47
  hl-color:: red
- Writing your first pipeline
  ls-type:: annotation
  hl-page:: 47
  hl-color:: yellow
- most important parts here
  ls-type:: annotation
  hl-page:: 47
  hl-color:: yellow
- create a Pipeline object
  ls-type:: annotation
  hl-page:: 48
  hl-color:: yellow
- read this input from the resource called lorem.txt
  ls-type:: annotation
  hl-page:: 48
  hl-color:: yellow
- start filling it with data
  ls-type:: annotation
  hl-page:: 48
  hl-color:: yellow
- Each `PCollection` object (that is, parallel collection) can be imagined as a line (an edge) connecting two vertices(`PTransforms`, or parallel transforms) in the pipeline's DAG
  hl-stamp:: 1670900814730
  hl-page:: 48
  ls-type:: annotation
  hl-color:: green
- takes raw input from the list and creates a new PCollection
  ls-type:: annotation
  hl-page:: 49
  hl-color:: yellow
- [:span]
  ls-type:: annotation
  hl-page:: 49
  hl-color:: yellow
  hl-type:: area
  hl-stamp:: 1670900975910
- main output(PCollection of PTransform, called Create) is not presently consumed by any PTransform
  ls-type:: annotation
  hl-page:: 49
  hl-color:: yellow
- This creates a new PTransform (Tokenize) and connects it to our input PCollection
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
- [:span]
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
  hl-type:: area
  hl-stamp:: 1670901628516
- Tokenize `PTransform` **takes input lines of text and splits each line into words**, which **produces a new `PCollection` that contains all of the words** from all the lines of the input `PCollection`
  hl-page:: 50
  ls-type:: annotation
  hl-color:: yellow
- produce the well-known word count example
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
- simply print the output PCollection to standard output
  ls-type:: annotation
  hl-page:: 50
  hl-color:: yellow
- [:span]
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
  hl-type:: area
  hl-stamp:: 1670901970099
- This causes the pipeline to be passed to a runner (configured in the pipeline
  ls-type:: annotation
  hl-page:: 51
  hl-color:: green
  hl-stamp:: 1670902077557
- The standard default runner is the DirectRunner, which executes the pipeline in the local Java Virtual Machine (JVM) only
  ls-type:: annotation
  hl-page:: 51
  hl-color:: yellow
- The ordering of output is not defined and is likely to vary over multiple runs. This is to be expected and is due to the fact that the pipeline underneath is executed in multiple threads.
  ls-type:: annotation
  hl-page:: 52
  hl-color:: yellow
- simplified to the following:
  ls-type:: annotation
  hl-page:: 52
  hl-color:: yellow