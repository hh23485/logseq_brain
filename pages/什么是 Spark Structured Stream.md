tags:: [[Spark Structured Streaming]]

- 发展
	- #+BEGIN_QUOTE
	  基于 Spark SQL 引擎和 DataFrame API，Spark 2.0 引入了实验性的连续流处理模型和结构化流处理 API。到 Spark 2.2 版本，结构化流处理（Structured Streaming）已经到了一般可用的状态...
	  Spark 2.x 和 Spark 3.0 将流式数据源的范围扩大到包括 Apache Kafka、Kinesis、基于 HDFS 的数据，以及云存储的数据
	  #+END_QUOTE
- 能力
	- 让大数据开发人员能够将来自 [[Kafka]] 或其他流数据形式的数据源和静态数据结合起来，并实时响应
	- 模型将数据流视为持续增长的表，新的数据记录不断增加到表的最后，因此可以将流也当做结构化的表一样，直接使用 [[Spark SQL]] 查询即可
	- 在结构化流的模型下， [[Spark SQL]] 也会负责处理容错、迟到数据语义的方方面面，以让开发人员只关注于处理流数据本身
- 实例
	- 从本机的套接字读取数据 (来自 [[Learning Spark 2nd@Book]] )
	- ```  python
	  # Python代码
	  # 从本机读取一个数据流
	  from pyspark.sql.functons import explode, split
	  lines = (spark
	  	.readStream
	      .format("socket")
	      .option("host", "localhost")
	      .option("port", 9999)
	      .load())
	  # 执行转化操作
	  # 将每行字符切分为单词
	  words = lines.select(explode(split(lines.value, " ")).alias("word"))
	  # 生成流式单词统计
	  word_counts = words.groupBy("word").count()
	  # 将输出写入Kafka数据流
	  query = (word_counts
	          	.writeStream
	          	.format("kafka")
	  			.option("topic", "output"))
	  ```
	-