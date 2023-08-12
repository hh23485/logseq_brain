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
	- Data Parallelization / Vectorization
	- Code Specialization / Compilation