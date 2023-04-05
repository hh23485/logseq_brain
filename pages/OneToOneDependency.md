tags:: Spark

- 一对一依赖：一对一依赖表示 child RDD 和 parent RDD 中的分区个数相同，并存在一一映射关系
- 典型的 transformation 包括 [[map]]、 [[filter]]