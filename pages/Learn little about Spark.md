tags:: Spark, Sharing

- TOC {{renderer :tocgen, [[]], 2, h}}
- [[Spark]] is a big data framework, a multi-language engine for executing data engineering, data science, and machine learning on single-node machines or clusters. In this page,  I want to introduce some **basic concepts of Spark**, some key architectures and how to run on MT to help you better understand and get started with Spark.
- # Quick Introduction about Why Spark
  collapsed:: true
	- ## Start from MapReduce
	  collapsed:: true
		- **MapReduce** is a programming model and software framework first introduced by **Google** in 2004 to address the challenges of processing large data sets. The main idea behind MapReduce is to **divide a large task into smaller subtasks that can be processed in parallel across multiple computing nodes.**
		- Why was it introduced?
			- To address the challenges of processing large data sets efficiently.
		- How does it work?
			- Here is a [simple brief of MapReduce](https://hci.stanford.edu/courses/cs448g/a2/files/map_reduce_tutorial.pdf)
			- Use a unified abstraction, there are two phases: map and reduce.
				- The map function processes input data and generates intermediate key-value pairs.
				- The reduce function aggregates the intermediate results to produce the final output.
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
		- Just write how to deal with action like local simple functions, no worry about these ((6425b521-2d4b-4ad3-8acb-57489ff1f572))
			- Write Map function
			- Write Reduce function
		- Common features of big data frameworks #.ol
			- **Distributed computing**: Big data frameworks enable parallel processing of data across multiple nodes in a cluster.
			- **Fault tolerance**: Big data frameworks can handle node failures in a cluster and automatically reassign work to other nodes.
			- **Data storage and management**: Big data frameworks provide tools for storing and managing large amounts of data across distributed systems.
			- **Data processing and analysis**: Big data frameworks offer a wide range of tools for processing and analyzing data at scale.
	- ## Why use Spark instead of MapReduce?
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
		- ### Map Reduce Version
			- #### Java
			  collapsed:: true
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
			  collapsed:: true
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
		- Create a project, and paste the code in
		- Local
			- Run directly in IDE
		- Remote
			- Submit to spark endpoint
- # Spark Internal Basic
	- All this content comes from a great book [大数据处理框架Apache Spark设计与实现（全彩） (豆瓣) (douban.com)](https://book.douban.com/subject/35140409/)
	- ## How a Spark application run?
		- Here are the steps
			- An big data application can be describe as <Input Data, User Source Code, Configuration and Arguments>
				- Input data are hosted in HDFS or generated in the code
			- Once submit to Spark, it will create a [Driver]([[Spark Driver]]) to deal follow actions: #.ol
				- analysis and **convert** them into spark **logic plan**, which means the calculate steps, will be kind DAG.
				- Based on logic plan, spark will **convert** the logic plan **to physical plan**, which means how to execute the job
				- Request for **resources**, **schedule** executors and **run** it
				- Collect result.
		- Fig about the execute mode
			- ![image.png](../assets/image_1680199915800_0.png){:height 278, :width 599}
		- Fig about the system layer
			- ![image.png](../assets/image_1680199082879_0.png)
	- ## What's RDD
		-
	- ## What's the deployment mode of Spark
	- ## What's the architecture of Spark from high level
	- ## How Spark generate logic plan
	- ## How spark convert logic plan to physical plan
	- ## How spark do shuffle
	- ## How Spark do caching
	- ## How Spark do fault tolerance
	- ## How Spark manage memory
	- Big data application 3 elements:
		- **Input Data**: Stored in DFS, like HDFS, cosmos
		- **User Source Code**
		- **Configuration**
	- Big data framework has four layers:
		- User Layer
		  Distributed Data Parallel Processing Layer
		  Resource management and task scheduling layer
		  Physical execution layer
	-
- # Spark Internal
	- [[What's RDD]]
	- [[]]
- # Practice
	- [[Write a Spark job on MT in 5 minutes]]
	- [[What happened in Spark - SparkUI]]
	-