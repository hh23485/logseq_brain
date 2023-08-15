tags:: [[CMU 15-721]]

- ## 观察
	- I/O 是目前 query 主要的瓶颈
	- 当必须读取数据时，我们希望能从其中读取足够多的有效信息，不浪费 IO
- ## 任何压缩必须要实现的目标
	- 必须压缩为固定长度
	- 必须是无损的压缩
	- 尽可能晚的推迟在查询时的解压缩，也就是尽可能多的操作想要在解压操作上处理，如果必须要读取，才解压缩数据
- ## 压缩的粒度
	- Block-Level
		- database page or row group
	- Tuple-Level
		- content of the entire tuple in MSN only
	- Attribute-Level
		- Single attribute value within one tuple
		- Multiple attributes for the same tuple
	- Column-Level
		- Multiple value for one or mote attributes for multiple tuples for DSM only
- ### 朴素压缩
	- 使用通用的压缩方法，直接压缩输入数据
		- LZO, LZ4, Snappy, Brotli, Oracle OZIP, Zstd.
			- Snappy 是其中最广泛使用的算法之一
			- 但最新的的压缩性能和压缩比的权衡的是 Zstd
	- 这不是一个好方法
		- MySQL 中存储压缩数据，每个 page 在内存中大约 16 KB，但存储到磁盘后，是 1,2,4,8 KB 大小中的一个
			- MySQL 在内存中会有一个 mod log 区域，这个位置存放了所有的更新的信息，那么，如果有人放入了更新操作或者删除操作，那么在内存中就可以直接获得结果
			- 这些块就是B+树的节点
			- 缺点
				- 但在想要读取压缩的中的数据时，仍然需要先解压缩，因为其中压缩的结构并不能被数据系统读取和识别，是算法压缩完的字节块而已
				- 如果我想要读取16KB中的1KB的某部分数据，是做不到的
- ## 列式压缩
	- ### Run-length Encoding
		- 如果列已经排序了，那么可以对相邻相同的数据进行合并
		- 三元组为 (value, offset, count)
			- ![image.png](../assets/image_1692090443097_0.png)
		- 但很难，因为通常值列不会被排序，大多是排序主键列
			- ![image.png](../assets/image_1692090383638_0.png)
	- Dictionary Encoding
		- 使用一个字典来描述某个较短的代号到某个频繁实际值的映射关系
		- Build dictionary
			- All at once
			  logseq.order-list-type:: number
			- Incremental
			  logseq.order-list-type:: number
		- 压缩范围
			- Block-level
				- 每个块有自己的 dictionary
				- 不过如果要做 join，那么必须得解压缩数据了，因为多个 block 之间的相同的 key 并不能代表 value 也相同
			- Table-level
				- 每个表有自己的 dictionary
			- Multi-Table
				- 多个表共享一个 dictionary
			- 编码
				- 例如
					- ![image.png](../assets/image_1692091558439_0.png)
				- 有的操作，例如上图中的 `DISTINCT`，可以让查询只在字典上发生，而不需要查询原始数据
			- 数据结构
				- 数组
				  logseq.order-list-type:: number
					- 如果数据不变，那么会是个不错的选择
						- ![image.png](../assets/image_1692092096791_0.png){:height 480, :width 411}
				- 哈希表
				  logseq.order-list-type:: number
				- B+ 树
				  logseq.order-list-type:: number
				-
	- Bitmap Encoding
	- Delta Encoding
	- Bit Packing