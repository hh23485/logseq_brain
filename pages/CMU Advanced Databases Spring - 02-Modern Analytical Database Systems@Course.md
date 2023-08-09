tags:: [[15-721]]

- Course Outline
	- ![image.png](../assets/image_1691571991621_0.png)
- Distributed query execution
	- OLAP 查询在分布式数据库上执行和单点的 DBMS 是类似的
	- 像一个 DAG 一样执行各个操作
		- Table Scan
		- Join
		- Aggregation
		- Sorting
	- 执行过程的宏观过程
		- 将 Query 发送给一些节点，每个节点收到其中一些输入和指定的运算，得到运算结果
		- 这些结果视作中间结果，然后根据执行计划来决定下一个操作，也许是发送给某个节点，也许是 shuffle
		- 执行 DAG 下一个步骤
		- 聚合结果
		- ![image.png](../assets/image_1691572650115_0.png)
-