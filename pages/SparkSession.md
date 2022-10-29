tags:: Spark

- 作用
	- SparkSession 自 Spark 2.0 后，就是 Spark 所有操作和数据的统一入口
		- 只需要为每个 JVM 创建一个 SparkSession 对象，然后就可以用其执行各种 Spark
- Notice
	- 虽然 SparkSession 承担了统一入口的职责，但为了保证 Spark 代码的向后兼容，原来的 Context 对象仍然可以访问
	- 在 Spark shell 中 SparkSession 会被自动创建，只需要使用全局变量 `spark` 或 `sc` 即可
- 示例
	- ``` scala
	  // Scala代码
	  import org.apache.spark.sql.SparkSession
	  // 构建Spark
	  Sessionval spark = SparkSession
	      .builder
	      .appName("LearnSpark")
	      .config("spark.sql.shuffle.partitions", 6)
	      .getOrCreate()
	  ...
	  // 用session对象读取
	  JSONval people = spark.read.json("...")
	  ...
	  // 用session对象发起SQL查询
	  val resultsDF = spark.sql("SELECT city, pop, state, zip FROM table_name")
	  ```
	-