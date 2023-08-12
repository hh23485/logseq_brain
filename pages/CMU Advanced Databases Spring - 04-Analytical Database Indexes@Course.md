tags:: [[CMU 15-721]]

- 和 OLTP 相比，OLAP 的查询会有许多不同
	- 很少单点查询，大多扫描数据
	- 几乎不会更新数据
- 对顺序扫描的优化方法
	- Data Prefetching
	- Task Parallelization / Multi-threading
	- Clustering / Sorting
	- Late Materialization
	- Materialized Views / Result Caching
	- Data Skipping
	  id:: 64d7aa48-fea6-41fd-ab6f-e1f44888dbf3
	- Data Parallelization / Vectorization
	- Code Specialization / Compilation
- ((64d7aa48-fea6-41fd-ab6f-e1f44888dbf3))
	- Approximate Queries
		- 例如在一个子集上执行来获得近似的结果
			- 对于对结果不需要太精确的场景下是可行的，比如想要获得网站的访问量
	- Data Pruning
		- 通过一些数据结构、算法过滤来跳过对某些数据的访问
		- 需要权衡范围/效率，手动/自动
	-