tags:: Spark SQL

- Spark SQL 是Spark 提供的 [4 个组件](((635ca90b-779c-481f-9e4b-88aa7ef5401a))) 之一
- 能力
	- 非常适合处理结构化数据
	- 可以将关系型数据库的表或结构化文件都读取并抽象为 Spark 的**永久表**或**临时表**
	- 可以使用 Spark 提供的各种编程语言直接使用 SQL 查询来访问 DataFrame 数据
- 例子
	- 使用 Scala + SQL 查询访问 DataFrame
	  ```  scala
	  // Scala代码
	  // 从亚马逊云 S3 存储桶加载数据为Spark DataFrame
	  spark.read.json("s3://apache_spark/data/committers.json").createOrReplaceTempView("committers") // 发起SQL查询，并以Spark DataFrame的形式返回结果
	  val results = spark.sql("""
	  SELECT name, org, module, release, num_commits
	  FROM committers
	  WHERE module = 'mllib' 
	  	  AND num_commits > 10
	  ORDER BY num_commits DESC
	  """)
	  ```
		- 从 S3 中读取 JSON 数据
		- 创建临时表
		- 使用 SQL 查询
		- 结果由 Spark DataFrame 表示
-