tags:: [[15-445]], [[Course]]

- Table index
	- Replicas of some attribution in a sorted way for quicker accessing.
- B-tree family
	- 通常在数据库领域提及 b-tree，指的就是 [[B+ 树]]
- B+ 树
	- 平衡树
	- 有序的
	- 访问、删除、插入的时间复杂度都是 O(log n)
	- 每层有多个分支
		- 在一个块上存储更多的节点，减少总访问的随机访问次数
		-