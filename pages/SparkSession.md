tags:: Spark

- 作用
	- SparkSession 自 Spark 2.0 后，就是 Spark 所有操作和数据的统一入口
- Notice
	- 虽然 SparkSession 承担了统一入口的职责，但为了保证 Spark 代码的向后兼容，原来的 Context 对象仍然可以访问
- 示例
	-