tags:: Spark

- 作用
	- 负责初始化 [[SparkSession]]
	- 与集群管理器打交道，向集群管理器申请 Spark 执行器 (JVM) 所需要的资源 (CPU、内存)
	- 将所有的 Spark 操作转换为 DAG 运算
	- 负责调度
	- 将计算分成任务分发到 Spark 执行器上，并直接与执行器通讯
	-