tags:: Spark, Sharing

- TOC {{renderer :tocgen, [[]], 4, h}}
- [[Spark]] is a big data framework, a multi-language engine for executing data engineering, data science, and machine learning on single-node machines or clusters. In this page,  I want to introduce some **basic concepts of Spark**, some key architectures and how to run on MT to help you better understand and get started with Spark.
- # Introduce of Spark
	- TODO Add some latest status of Spark
	- ## Spark news
	- ## Spark capabilities
		- [Home page of Spark](https://spark.apache.org/docs/latest/index.html)
	- ## Quick examples
- # Quick Introduction about Why Spark
  collapsed:: true
	- ## Start from MapReduce
	  collapsed:: true
		- **MapReduce** is a programming model and software framework first introduced by **Google** in 2004 to address the challenges of processing large data sets. The main idea behind MapReduce is to **divide a large task into smaller subtasks that can be processed in parallel across multiple computing nodes.**
		- Why was it introduced?
			- To address the challenges of processing large data sets efficiently.
		- How does it work?
			- Here is a [simple brief of MapReduce](https://hci.stanford.edu/courses/cs448g/a2/files/map_reduce_tutorial.pdf)
			- Use a unified abstraction, there are two phases: **map** and **reduce**.
				- The **map** function **processes input data and generates intermediate key-value pairs.**
				- The **reduce** function **aggregates the intermediate results to produce the final output.**
			- Example: **[Word Counting]([[An Example of word count on MapReduce]])**
				- {{embed ((6425a352-7bfd-4b83-bc9c-a65c6b0f2856))}}
		- Benefits of using MapReduce
			- **Simplification of programming model**
			- **Scalability**
			- **Independence of tasks**
		- Beside the framework, MapReduce is simple to simulate in python or other languages, why we still need the framework, then why Spark?
	- ## Example on such job without big data framework
	  collapsed:: true
		- A Data Generate Job in Azure Speller
			- Convert a few big language model data into [[RocksDB]] directories
				- Each line is a Key Value pair
				- Max file is about 600-800GB
				- Use hash to split into 1000-10000 parts
				- Download from cosmos, and upload to cosmos
			- Challenges #.ol
			  id:: 6425b521-2d4b-4ad3-8acb-57489ff1f572 #.ol
				- How to read/write faster?
				- How to utilize resources as much as possible?
				- How to avoid exceeding the memory limit?
				- How to balance read and write speeds? RocksDB need compact.
				- How to avoid thread competition and safety issues?
				- How to debug?
				- How to support partitioning methods other than Hash, such as Range?
				- How to download and upload quickly?
				- How to avoid failure because WIndows can only open 8000 files?
				- How to recover from a failure?
				- How to run on multiple machines?
			- ![Slide5.jpg](../assets/Slide5_1680192445315_0.jpg)
	- ## Why need big data framework like MapReduce?
	  collapsed:: true
		- Just write how to deal with action like local simple functions, no worry about these ((6425b521-2d4b-4ad3-8acb-57489ff1f572))
			- Write Map function
			- Write Reduce function
		- Common features of big data frameworks #.ol
			- **Distributed computing**: Big data frameworks enable parallel processing of data across multiple nodes in a cluster.
			- **Fault tolerance**: Big data frameworks can handle node failures in a cluster and automatically reassign work to other nodes.
			- **Data storage and management**: Big data frameworks provide tools for storing and managing large amounts of data across distributed systems.
			- **Data processing and analysis**: Big data frameworks offer a wide range of tools for processing and analyzing data at scale.
	- ## Why use Spark instead of MapReduce?
	  collapsed:: true
		- MapReduce has some drawbacks in its implementation
			- Map Reduce has limited expressive power, while many data processing requires higher-level expressions, such as `Join`, `Zip`, `FlatMap`, `Sum`, `Max`, etc.
			  background-color:: red
				- Scope and Spark allowed users to write code like SQL, and high level operations.
				  background-color:: green
			- Map Reduce can only express one operation per task, and often data processing may contain multiple operations. While Map Reduce itself cannot concatenate and organize.
			  background-color:: red
				- Scope and Spark will convert the job to DAG.
				  background-color:: green
			- Map Reduce is not faster enough compare to Spark.
			  background-color:: red
				- Spark will use memory as much as possible, also support pipeline execution.
				  background-color:: green
	- ## Write WordCount in Map Reduce and Spark
	  collapsed:: true
		- ### Map Reduce Version
			- #### Java
				- ``` java
				  public static class WordCountMapper extends Mapper<LongWritable, Text, Text, IntWritable> {
				      private final static IntWritable one = new IntWritable(1);
				      private Text word = new Text();
				  
				      public void map(LongWritable key, Text value, Context context) throws IOException, InterruptedException {
				          String line = value.toString();
				          StringTokenizer tokenizer = new StringTokenizer(line);
				          while (tokenizer.hasMoreTokens()) {
				              word.set(tokenizer.nextToken());
				              context.write(word, one);
				          }
				      }
				  }
				  
				  public static class WordCountReducer extends Reducer<Text, IntWritable, Text, IntWritable> {
				      private IntWritable result = new IntWritable();
				  
				      public void reduce(Text key, Iterable<IntWritable> values, Context context) throws IOException, InterruptedException {
				          int sum = 0;
				          for (IntWritable val : values) {
				              sum += val.get();
				          }
				          result.set(sum);
				          context.write(key, result);
				      }
				  }
				  ```
		- ### Spark Version
			- #### Java
				- ``` java
				  import org.apache.spark.SparkConf;
				  import org.apache.spark.api.java.JavaRDD;
				  import org.apache.spark.api.java.JavaSparkContext;
				  
				  public class WordCount {
				      public static void main(String[] args) {
				          // Create a SparkConf object and set the app name
				          SparkConf conf = new SparkConf().setAppName("WordCount");
				  
				          // Create a JavaSparkContext object
				          JavaSparkContext sc = new JavaSparkContext(conf);
				  
				          // Load the input text file into an RDD
				          JavaRDD<String> input = sc.textFile(args[0]);
				  
				          // Split each line into words
				          JavaRDD<String> words = input.flatMap(line -> Arrays.asList(line.split(" ")).iterator());
				  
				          // Map each word to a tuple of (word, 1)
				          JavaPairRDD<String, Integer> pairs = words.mapToPair(word -> new Tuple2<>(word, 1));
				  
				          // Reduce by key to get the count of each word
				          JavaPairRDD<String, Integer> counts = pairs.reduceByKey((a, b) -> a + b);
				  
				          // Save the output to a text file
				          counts.saveAsTextFile(args[1]);
				  
				          // Stop the SparkContext
				          sc.stop();
				      }
				  }
				  ```
			- #### Python
				- ``` python
				  from pyspark import SparkConf, SparkContext
				  
				  # Create a SparkConf object and set the app name
				  conf = SparkConf().setAppName("WordCount")
				  
				  # Create a SparkContext object
				  sc = SparkContext(conf=conf)
				  
				  # Load the input text file into an RDD
				  input = sc.textFile("input.txt")
				  
				  # Split each line into words
				  words = input.flatMap(lambda line: line.split(" "))
				  
				  # Map each word to a tuple of (word, 1)
				  pairs = words.map(lambda word: (word, 1))
				  
				  # Reduce by key to get the count of each word
				  counts = pairs.reduceByKey(lambda a, b: a + b)
				  
				  # Save the output to a text file
				  counts.saveAsTextFile("output")
				  
				  # Stop the SparkContext
				  sc.stop()
				  ```
			- ### Scala
			  collapsed:: true
				- ``` scala
				  import org.apache.spark.{SparkConf, SparkContext}
				  
				  object WordCount {
				    def main(args: Array[String]) {
				      // Create a SparkConf object and set the app name
				      val conf = new SparkConf().setAppName("WordCount")
				  
				      // Create a SparkContext object
				      val sc = new SparkContext(conf)
				  
				      // Load the input text file into an RDD
				      val input = sc.textFile(args(0))
				  
				      // Split each line into words
				      val words = input.flatMap(line => line.split(" "))
				  
				      // Map each word to a tuple of (word, 1)
				      val pairs = words.map(word => (word, 1))
				  
				      // Reduce by key to get the count of each word
				      val counts = pairs.reduceByKey(_ + _)
				  
				      // Save the output to a text file
				      counts.saveAsTextFile(args(1))
				  
				      // Stop the SparkContext
				      sc.stop()
				    }
				  }
				  ```
	- ## We got the code, how to run it?
	  collapsed:: true
		- Create a project, and paste the code in
		- Local
			- Run directly in IDE
		- Remote
			- Submit to spark endpoint
- # Spark Internal Basic
	- All this content comes from a great book [[大数据处理框架 Apache Spark 设计与实现@Book]]
	- ## How a Spark application run?
	  collapsed:: true
		- Here are the steps:
			- An big data application can be describe as <`Input Data`, `User Source Code`, `Configuration`>
				- Input data are hosted in HDFS or generated in the code
				- Configurations are resource related, like buffer size, memory limit, CPU, instance number, dependency files
			- Once submit to Spark, it will create a [Driver]([[Spark Driver]]) to deal follow actions: #.ol
				- Analyze and **convert** them into spark **logic plan**, which means the **Actions** and **Orders**.
				- Based on logic plan, spark will **convert** the logic plan **to physical plan**, which means how to execute the job
				- Request for **resources**, **schedule** executors and **run** it
				- Collect result.
		- Fig about the progress
			- ![image.png](../assets/image_1680201501252_0.png){:height 384, :width 699}
			  id:: 6425d71c-9fe1-43f5-b43e-dbffd4e28a56
		- Fig about the execute mode
		  collapsed:: true
			- ![image.png](../assets/image_1680199915800_0.png){:height 278, :width 599}
		- Fig about the system layer
		  collapsed:: true
			- ![image.png](../assets/image_1680199082879_0.png)
	- ## What's RDD
	  collapsed:: true
		- [[RDD]], full name is [[Resilient Distributed Dataset]], is a fundamental abstract data structure in Spark.
		- Putting aside those concepts in the official introduction, the RDD is a object with partition information, with such features:
			- Stands for a collection, different type RDD implements express different collections
			- **Immutable**, for parallel computation
			- Contains **partition information**, like partition list, partitioner
			- Contains dependency **relationships with parent RDDs**
			- Contains **some partition data**
			- **Operations** are defined on the RDD, like `rdd.Count()`, `rdd.Filter()`, `rdd.GroupByKey()`
		- Because RDDs contain this information, they can adequately represent the dataset in a distributed computation and thus be the data abstraction for all intermediate results.
			- {{embed ((6425d71c-9fe1-43f5-b43e-dbffd4e28a56))}}
				- The squares represent java objects
				- **The circles are RDDs**
		- RDDs are created by an API provided by Spark, and can be constructed from ordinary in-memory object data, or from files, streams.
			- Create from HDFS file
				- ``` java
				  // Load data from an HDFS file into an RDD
				  JavaRDD<String> lines = sc.textFile("hdfs://path/to/input/file.txt");
				  ```
			- Create from a array
				- ``` java
				  // Load data from a Java memory array into an RDD
				  Integer[] data = new Integer[]{1, 2, 3, 4, 5};
				  JavaRDD<Integer> rdd = sc.parallelize(Arrays.asList(data));
				  ```
	- ## What's the deployment mode of Spark
	  collapsed:: true
		- Big data frameworks are almost always deployed in master-slave mode, and when Spark is deployed in a cluster, it looks like the following diagram
			- ![image.png](../assets/image_1680201992563_0.png){:height 598, :width 752}
		- ### Master node and Worker node
		  collapsed:: true
			- **Master node** is responsible for managing applications and tasks
				- The Master node has a resident **Master process** on it
				- Responsible for managing all Worker nodes
				- Assigning Spark tasks to Worker nodes
				- Collecting information about the operation of tasks on Worker nodes
				- Monitor the survival status of Worker nodes, etc.
			- **Worker nodes** are responsible for executing tasks
				- Resident worker processes on worker nodes
				- Communicate with the Master node
				- Responsible for managing the execution of Spark tasks
					- e.g. start Executor to execute specific Spark tasks
					- Monitoring the status of tasks, etc.
		- ### When Spark cluster starts
		  collapsed:: true
			- The Master process is started on the Master node
			- The Worker process is started on each Worker node
		- ### When submit applications
		  collapsed:: true
			- Create a **driver** process (which run the `main()` of application)
			- Driver on **master node** notify **worker node** to start **executors**, **executors will take up declared resources**
			- Executors run tasks as threads, 1 CPU per task. All the tasks belong to the same job.
		- TODO OnYarn
		- ### Summary
			- 一个农场主(`Master`)有多片草场(`Worker`),农主要把草场租给 3 个牧民来放马、牛、羊。假设现在有3个项目(`Application`)需要农主来运作:第1个牧民需要一片牧场来放 100 匹马,第2个牧民需要一片牧场来放 50 牛,第 3 个牧民需要一片牧场来放80只羊
				- 每个牧民可以看作是一个`Driver`,而马、牛、可以看作是task。为了保持资源合理利用、避免冲突,在放牧前,农场主需要根据项目求为每个牧民划定可利用的草场范围,而且尽量让每个牧民在每个草场都有一小片可放的区域(`Executor`)
				- 在放牧时,每个牧民(`Driver`)只负责管理自己的动物(`Task`)
				- 农场主(`Master`)负责监控草场(`Worker`)、牧民(`Driver`)等状况
	- ## A new example with more actions for analysis
	  collapsed:: true
		- Let's give an example for further analysis. It's a dummy code, without any meanings, just generate a RDD with randomly int, then run `RDD.count` and `RDD.groupByKey`.
			- ``` scala
			  def main(args: Array[String]): Unit = {
			      // setup spark context
			      val spark = SparkSession
			          .builder
			          .appName("Spark basic example")
			          .getOrCreate()
			  
			      val numMappers = 3
			      val numKVPairs = 4
			      val valSize = 1000
			      val numReducers = 2
			      val input = 0 until numMappers // input is [0, 1, 2]
			  
			      // generate a rdd
			      val pairs = spark.sparkContext.parallelize(input, numMappers).flatMap { p =>
			          val ranGen = new Random
			          val arr1 = new Array[(Int, Array[Byte])](numKVPairs)
			          for (i <- 0 until numKVPairs) {
			              val value = new Array[Byte](valSize)
			              ranGen.nextBytes(value)
			              arr1(i) = (ranGen.nextInt(numKVPairs), value)
			          }
			          arr1
			      }.cache()
			  
			      // pairs is an rdd with numMappers * numKVPairs elements
			      // each element is a tuple of (Int, Arrat[Byte]), as well as a key-value pair
			      // key is between 0 and numKVPairs - 1
			      // value is an array of bytes of length valSize
			  
			      println(pairs1.count())
			      println(paris1.toDebugString)
			      val results = paris1.groupByKey(numReducers)
			      println(results.count())
			      println(results.toDebugString)
			      spark.stop()
			  }
			  ```
		- ### What's the logic plan and physical plan will be?
		  collapsed:: true
			- Ideally the **steps** will be like:
				- ![image.png](../assets/image_1680538845294_0.png){:height 519, :width 854}
			- Little more dtails
				- Before `paris1.count()`, the calculation has not started. That's [functional programming](https://www.databricks.com/session/spark-as-the-gateway-drug-to-typed-functional-programming).
				- Here is a `cache()` a important ability of Spark
			- #### Let's run it, then we can go to Spark UI and see what's happening
				- TODO graph of jobs
					- Here are two jobs, `pairs1.count()` and `results.count()`
					- The two jobs has different number of stages
				- TODO debug string
					- Different types of RDD
			- #### Logic Plan Summary
				- Focus on **Data Source**, **Data Model**, **Data Action**, **Result**
					- **Data Source**: Generated inputs
					- **Data Model**: RDDs
					- **Data Action**: [Transform]([[Spark Transformation]]) like `flatMap`, [Action]([[Spark Action]]) like `count`
					- **Result**: Final result
				- Job0: input -> [[ParallelCollectionRDD]] -> [[MapPartitionsRDD]]
					- ![image.png](../assets/image_1680540692648_0.png){:height 409, :width 688}
				- Job1: input -> [[ParallelCollectionRDD]] -> [[MapPartitionsRDD]] -> [[ShuffledRDD]]
					- ![image.png](../assets/image_1680691483961_0.png)
			- #### Physical Plan Summary
				- Focus on stages and task level
				- For Job 0
					- has 2 RDDs, merged in 1 stage
					- has 3 tasks
					- Driver collects all results together and final result
				- For Job 1
					- Has 2 stages
						- Stage0 contains 3 tasks, 1 RDD
						- Stage 1 contains 2 tasks, 1 RDD
				- Shuffle happened here for Job1-Stage1 to find data from Job1-Stage0
					- First RDD each partition in stage1 get **parts of data** from all stage 0 final RDD partitions
					  id:: 642b070f-4959-4b7d-97e0-2729fcfc1d7b
					- TODO add graph
				- Task in the same stage can run in parallel
			- Questions
				- How the job, stage, task decided?
				- How shuffle implements?
	- ## How Spark generate logic plan
	  collapsed:: true
		- Three main questions:
			- ((642b08b1-2a52-46c9-99ac-8761c0226e48))
			- ((642b08d0-4f08-42de-b18a-6673f7cf17c6))
			- ((642b0905-d68b-416a-9c13-a0059627f221))
		- ### How to generate RDD, which kind RDD should be generated?
		  id:: 642b08b1-2a52-46c9-99ac-8761c0226e48
			- [[RDD]]s support two types of operations: *[transformations]([[Spark Transformation]])*, which create a new dataset from an existing one, and *[actions]([[Spark Action]])*, which return a value to the driver program after running a computation on the dataset.
			- Different transformation will generate different types of RDD
				- [What's tansformation?](((642cd333-da61-467c-8d3a-f18b14c1a8ca)))
				- [Kinds of transformation](((642ce69a-00d6-4762-8ff3-12ff3349c8ea)))
		- ### How to build RDD relationships
		  id:: 642b08d0-4f08-42de-b18a-6673f7cf17c6
			- Questions
				- How to build relationships with RDD?
					- Could be `RDD1=>RD2`, or `(RDD1, RDD2) => RDD3` or even `(RDD1, RDD2, RDD3) => RDD4`, etc
				- How to decide how many partitions should be split in generated RDD?
					- If not specified, the new partitions number be the max partitions number in parent RDDs.
					- For parent RDDs, here are three common types of [partitioning method]([[Spark 如何划分 RDD 分区]])
				- What's the relationships between partitions in child RDD and parent RDDs?
					- Depends on transformation and parent RDDs' partition number
		- ### How to calculate RDD data?
		  id:: 642b0905-d68b-416a-9c13-a0059627f221
		  collapsed:: true
			- As long as we can deal RDD partitions number and relationships, spark can apply transformations and actions to each records.
			- logically, the progress just like apply function to local applications in such two ways:
				- ``` scala
				  int[] array = {1,2,3,4,5,6,7,8,9,10};
				  // map(func)
				  for (int i = 0; i < array.length; i++) {
				      newRecord = func(array[i]);
				      output(newRecord)
				  }
				  ```
					- ![image.png](../assets/image_1680679303732_0.png){:height 191, :width 445}
				- ``` scala
				  int[] array = {1,2,3,4,5,6,7,8,9,10};
				  // mapPartitions(func)
				  list[] newRecords = func(array);
				  output(newRecords)
				  ```
					- ![image.png](../assets/image_1680679276300_0.png){:height 164, :width 445}
			- For more details you can go to:
				- [Common use transformations]([[Spark 常见 Transformation]])
				- [Common use actions]([[Spark 常见 Action]])
		- From such transformations and actions, Spark shows a huge expressive improvement over MapReduce.
			- RDD vs <K, V>
			- High level transformation and action vs map() and reduce()
	- ## How spark convert logic plan to physical plan
	  collapsed:: true
		- ### How to split job, stage, and task?
			- Sorry but has to start another new code snippet
				- ![image.png](../assets/image_1680694684400_0.png){:height 665, :width 840}
				- code here
				  collapsed:: true
					- ``` scala
					  // Define an array of tuples with integer and character values
					  val data1 = Array[(Int, Char)] ((1, 'a'), (2, 'b'), (3, 'c'), (4, 'd'), (5, 'e'), (3, 'f'), (2, 'g'), (1, 'h'))
					  
					  // Parallelize the data and create an RDD with 3 partitions
					  val rdd1 = sc.parallelize(data1, 3)
					  
					  // Partition the RDD using a hash partitioner with 3 partitions
					  val partitionedRDD = rdd1.partitionBy(new HashPartitioner(3))
					  
					  // Define an array of tuples with integer and string values
					  val data2 = Array[(Int, String)] ((1, 'A'), (2, 'B'), (3, 'C'), (4, 'D'))
					  
					  // Parallelize the data and create an RDD with 2 partitions, then map each tuple to a new tuple with the second value repeated
					  val rdd2 = sc.parallelize(data2, 2).map(x => (x._1, x._2 + "" + x._2))
					  
					  // Define an array of tuples with integer and string values
					  val data3 = Array[(Int, String)] ((3, 'X'), (5, 'Y'), (3, 'Z'), (4, 'Y'))
					  
					  // Parallelize the data and create an RDD with 2 partitions
					  val rdd3 = sc.parallelize(data3, 2)
					  
					  // Union the two RDDs together
					  val unionedRDD = rdd2.union(rdd3)
					  
					  // Join the partitioned RDD with the unioned RDD
					  val resultRDD = partitionedRDD.join(unionedRDD)
					  
					  // Print the result RDD
					  resultRDD.foreach(println)
					  ```
				- This code contains such transactions
					- rdd1: `partitionBy`, `join`
					- rdd2: `map`, `union`, `join`
					- rdd3: `union`, `join`
			- 3 rules to split stages and tasks
				- Each action is a **Job**
				- Scan from back to front
					- when meet [[NarrowDependency]], merge into current **Stage**
						- RDD partition numbers are the same in a stage
					- when meet [[ShuffleDependency]], start a new **Stage**
				- Each partition is a **Task**
			- So in this case, the stages and tasks are like follows
			  collapsed:: true
				- ![image.png](../assets/image_1680695204114_0.png){:height 952, :width 945}
		- ### How to decided the tasks calculation order?
			- Stages will be scheduled as DAG
			- Tasks will be executed in parallel
		- ### How intermediate data is stored and calculated inside the task?
			- If each RDD is completely computed and then the value of the next RDD is computed, then once the RDD is very large, it will result in a large memory.
			- So Spark uses a pipelined approach to computing RDDs inside the task
			  background-color:: green
				- Abstract the transformation such pattern, `recordx` are records in first RDD, `f` is the first transformation, `g` is the second transformation.
					- `record1 => f(record1) => record1' => g(record1) => record1''`
					- `record2 => f(record2) => record2' => g(record2) => record2''`
					- `record3 => f(record3) => record3' => g(record3) => record3''`
					- ![image.png](../assets/image_1680696098159_0.png){:height 474, :width 784}
				- From this perspective, an idea is if `f` and `g` for `record1` are no need to care about `record2` and `record3`, then Spark no need to store all `recordX'`, all records can directly run both `f` and `g` separately.
				- Based on the idea, we can conclude from the characteristics of `f` and `g` as follows
					- if `f` and `g` only deal single record, no need to store record2, and record3. Run each records for all functions one by one, and only store final results.
					- if `g` ask for `recordX'`, have to store all `recordX` and recycle them after `g` done. This type of transformations are like [[mapPartitions]] and [[zipPafitions]]
					- if `f` ask for all `recordX`, have to read all records at first and recycle them after `g` done.
					- if `f` and `g` ask for all intermediate records, have to read and store all records at each step, and recycle them after done.
		- ### How to propagate intermediate data between stage?
			- Child RDD have to read data from parent RDD, these kind of information are stored in RDD.
			- Due to RDDs relationship between stages are [[ShuffleDependency]], upstream stage need to do [[Shuffle Write]]
				- Upstream need to  partition the output data for downstream, the partition number should the same with downstream stage partition number.
			- Then downstream stage need to read data from corresponding parent RDD, do [[Shuffle Read]]
				- Each partition need collect all needed data from multi upstream partitions through network
		- ### How to check physical plan?
			- Use [[Spark UI]]
				- Job information
				- Stage information
				- DAG Visualization
				- RDD in
				- Stage information
				- Task information
		- #+BEGIN_TIP
		  Adjust the order of transformation, may improve the performance.
		  #+END_TIP
		- #+BEGIN_WARNING
		  This only for RDD based operations, for Spark SQL, here are lots of other optimization methods.
		  #+END_WARNING
	- ## How spark do shuffle
		- Spark designed a general [[Shuffle Write]] framework
			- ![image.png](../assets/image_1680697497701_0.png)
			- From high level, here are 3 steps, aggregation (combine) and sort are optional #.ol
				- Use a Map liked collection to aggregate all records from map task (upstream calculation)
				- After aggregation, put the records into a Array liked array, and sort by `partitionId` or `partitionId + Key`
				- Output the records to disk files by `partitionId`
			- ### Shuffle Write without combine and sort
			  collapsed:: true
				- ![image.png](../assets/image_1680697921847_0.png){:height 432, :width 996}
				- Only need to partition data
					- Output each record to partition buffer
					- Once buffer is full, flush to disk
				- Spark use [[BypassMergeSortShuffleWriter]] do finsh this task.
				- Transformations
					- [[groupByKey]]
					- [[partitionBy]]
					- [[sortByKey]]
				- Shortage
				  background-color:: red
					- Need a buffer per partition, also a opened file, so only less than 200 partitions support.
			- ### Shuffle Write without combine but need sort
			  collapsed:: true
				- ![2023-04-05_20-37-37.jpg](../assets/2023-04-05_20-37-37_1680698329343_0.jpg){:height 468, :width 1031}
				- To sort the records, convert each `<K, V>` to `<(PID, K), V>`, and put into a Array ([[PartitionedPairBuffer]]).
					- Once the buffer is full, sort by `PID + key` and spill to disk.
					- Repeat until all output records are sorted by `PID + Key`, merge sort with disk files with memory ones
					- Write the outputs to disk single file, and keep each partition index.
				- [[PartitionedPairBuffer]] is a Array based on Memory and Disk
				- This shuffle write mode is [[SortShuffleWriter]](`KeyOrdering`=true).
				- Transformations
					- No default, but may implemented by users.
					- If modify the `KeyOrdering` to false, then support `groupByKey(300)`, `partitionBy(300)` and `sortByKey(300)`
				- Pros
				  background-color:: green
					- Use a array to support sort, easy to implements
					- Array size is under control.
					- Can support large partition due to the array support spill to disk.
			- ### Shuffle Write with combine, with or without sort by key
			  collapsed:: true
				- ![image.png](../assets/image_1680699138902_0.png){:height 433, :width 1103}
				- ![image.png](../assets/image_1680699232644_0.png){:height 430, :width 1115}
				- Use a new data structure [[PartitionedAppendOnlyMap]] to do combine.
					- PartitionedAppendOnlyMap is a special map like a `HashMap + Array`, support append records, and a sort after all records appended.
						- The HashMap is array based, when sorting, copy all object references to the front of array
							- ![image.png](../assets/image_1680699796317_0.png){:height 527, :width 876}
						- Then sort by Key or by Key's hash
						- Finally output all records from start to end.
					- When the map is full, will expand once, if not enough as well, will sort and spill all to disk.
						- ![image.png](../assets/image_1680700205410_0.png){:height 1113, :width 1079}
		- Spark designed a general [[Shuffle Read]] framework
			- ![image.png](../assets/image_1680700368922_0.png)
			- From high level, here are 3 steps, aggregation and sort are optional #.ol
				- Collect data from map tasks
				- Aggregation by key
				- Sort by Key
			- ### Shuffle Read without aggregation and sort
			  collapsed:: true
				- ![image.png](../assets/image_1680700449237_0.png){:height 584, :width 974}
				- Wait all map tasks to finish, and collect records to a buffer
				- Next operation will directly get records from buffer
				- Transformation
					- [[partitionBy]]
				- Pros
					- Simple
				- Cons
					- Not support sort and aggregation
			- ### Shuffle Read without aggregation but sort by key
			  collapsed:: true
				- ![image.png](../assets/image_1680701577652_0.png){:height 522, :width 1069}
				- Not like [[Shuffle Write]], [[Shuffle Read]] may need sort by `key` instead of `partitionId`
				- Records from buffer will be appended into a Array ([[PartitionedPairBuffer]])
					- Due to [[PartitionedPairBuffer]] is also designed for [[Shuffle Write]], the `partitionId` will be kept there
				- Sort and spill all the records to get final result
				- Transformations
					- [[sortByKey]]
					- [[sortBy]]
			- ### Shuffle Read with aggregation, with or without sort by key
			  collapsed:: true
				- ![image.png](../assets/image_1680701841734_0.png){:height 566, :width 1078}
				- ![image.png](../assets/image_1680701814101_0.png){:height 526, :width 1079}
				- Before sort, use a Map to do aggregation and sort
					- The data structure is [[ExternalAppendOnlyMap]], like [[PartitionedAppendOnlyMap]]. [[PartitionedAppendOnlyMap]] is for [[Shuffle Write]], support `partitionId`, while [[ExternalAppendOnlyMap]] not. All implement based on [[AppendOnlyMap]].
		- ### How to detect memory during shuffle?
			- Aggregation and sort collections are implemented based on [[AppendOnlyMap]]
			- It's hard to detect the actual memory cost of the collection, as the elements in it are reference instead of object, also the collection is updated all the time.
			- Before expends when collection is full, the map will check if the rest space is enough to double, then to decide whether spill to disk or not.
			- To detect the memory usage, [[AppendOnlyMap]] use sampling way to detect
				- Sampling object size in collection as current history size
				- When new record put in or updated, use history increasing volume + current size as new size
			- TODO Go to [[SizeTrackerEstimateSize]] function
	- ## How Spark do caching
		- ### Why Cache
			- ``` scala
			  // Define an input RDD with key-value pairs of Int and Char
			  val inputRDD = Array[(Int, Char)] ((1, 'a'), (2, 'b'), (3, 'c'), (4, 'd'), (5, 'e'), (3, 'f'), (2, 'g'), (1, 'h'), (2, 'i'), 3)
			  
			  // Map the input RDD to a new RDD with only the key-value pairs
			  val mappedRDD = inputRDD.map(x => (x._1, x._2))
			  
			  // Cache the mapped RDD in memory for faster access
			  // mappedRDD.cache()
			  
			  // Reduce the mapped RDD by key, concatenating the values with an underscore
			  val reduceRDD = mappedRDD.reduceByKey((x, y) => x + "_" + y, 2)
			  
			  // Print the reduced RDD
			  reducedRDD.foreach(println)
			  
			  // Group the mapped RDD by key, and convert the values to a list
			  val groupedRDD = mappedRDD.groupByKey(3).mapValues(V => V.tolist)
			  
			  // Print the grouped RDD
			  groupedRDD.foreach(println)
			  ```
			- The logic plan will like:
				- ![image.png](../assets/image_1680703547961_0.png){:height 747, :width 1064}
			- Here are two `foreach` jobs.
				- The two jobs shared the same process `inputRDD` => `mappedRDD`
				- However, spark will re-calculate the progress by default.
					- if the process is costly, use cache to skip the second time execution
					- if the process is quite cheap, re-run to avoid memory/disk waste
		- ### When to cache
			- To cache a RDD, you should call `rdd.cache()` before the action on the RDD.
				- In this case, you should call `mapped.cache` before the first `foreach`, else the cache will not be triggered.
		- ### Where to cache
			- .cache() is the same with `persist(MEMORY_ONLY)`
				- for MEMORY_ONLY, as long as the memory is not enough to store, will cancel this cache.
			- You can call `persist` with such parameters
				- ![image.png](../assets/image_1680704168703_0.png)
		- ### How to write cache
			- Write cache order:
				- After each records is calculated, will be write to cache store.
				- ![image.png](../assets/image_1680704552115_0.png){:height 685, :width 831}
			- For memory cache, here will be a memory area managed by [[BlockManager]] on each executor
				- BlockManager will have a memoryStore, which contains a `LinkedHashMap`
					- Key is blockId (`rddId + partitionId`)
					- Value is records of the partition
					- ![image.png](../assets/image_1680704568608_0.png)
				- LinkedHashMap implements LRU algo, that's how memory cache replacement policy.
		- ### How to read cache
			- `.cache()` will make the RDD, so when read data from child RDD, it will tell where the cached stored, and get from the executor.
				- Mark the cached partitions, memory size, etc.
			- ![image.png](../assets/image_1680704774043_0.png)
				- In this graph, the job2 task5 will read data from worker node 1 remotely, and task3 and task4 will directly read from local memory.
			- The read is record by record.
	- ## How Spark do fault tolerance
		- Re-run job
			- Requires **same input**, and the process should be **deterministic** and **idempotent**
		- Where to re-run from?
			- No Cache and Checkpoint
				- Re-run all jobs
			- Use Cache
				- Cache is perishable and can be lost for various reasons
					- LRU
					- Executor existed
			- Use Checkpoint
				- Persistence to distributed storage such as HDFS
				- The Stage that requires Checkpoint will be re-run to specifically write out the results, so you can add a cache to the first run to avoid repeated runs
				- Checkpoint will chop off the lineage
				- ![image.png](../assets/image_1680705385582_0.png){:height 735, :width 734}
- # Practice
	- [[Write a Spark job on MT in 5 minutes]]
	- TODO [[What happened in Spark - SparkUI]]