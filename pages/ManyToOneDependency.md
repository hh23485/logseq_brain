tags:: 窄依赖

- 多对一依赖：表示 child RDD 中的一个分区同时依赖多个 parent RDD 中的分区
	- ![image.png](../assets/image_1680663084057_0.png){:height 519, :width 361}
- 典型的 transformation 包括 [[cogroup]] 和 [[join]] 等