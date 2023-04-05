tags:: [[Spark Action]]

- # 常见的 Action
	- ## [[count]]，[[countByKey]] 和 [[countByValue]] 操作
		- `count(): long`
			- 语义: 统计`rdd1`中包含的 record 个数, 返回一个 `long` 类型
			- 用法: `val result = rdd1.count()`
			- `count()` 操作首先计算每个分区中 record 的数目,然后在 Dirver 端进行累加操作,得到最终结果
				- ![image.png](../assets/image_1680689449062_0.png){:height 446, :width 582}
		-
	-