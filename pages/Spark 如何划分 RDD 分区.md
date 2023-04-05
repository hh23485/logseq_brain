tags:: Spark, RDD, Partitioner

- 常见的 RDD 内部分区方法 (Partitioner) 包括如下几种
	- 水平划分
		- 例如 `parallelize(list(1,2,3,4,5,6,7,8,9), 3)` 就是将原始数据按下标分为 (1,2,3), (4,5,6), (7,8,9) 三组
		- 通常对于 HDFS 中的文件划分也是类似，将大文件按块长度直接切分为多个分区，默认 128MB 为单位进行切分
	- Hash 划分
	  alias:: HashPartitioner
		- 使用 record 的 Hash 值来进行划分，在给定的分区个数情况下，可以确定的将给定数据划分到某个分区
		- 但各个分区中的数据的个数和顺序不确定
		- 一般用于 Shuffle 阶段
	- 范围划分
	  alias:: RangePartitioner
		- 按元素大小关系划分，例如 [0, 100] 的随机数进行划分为 n 分，然后先将值域拆分，进而将每个元素放入对应的区域
		- 一般用于排序任务