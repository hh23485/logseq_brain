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
	  logseq.order-list-type:: number
	- 例如在一个子集上执行来获得近似的结果
		- 对于对结果不需要太精确的