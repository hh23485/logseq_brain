tags:: [[Python]], [[Books]]

- 第一章
	- namedtuple
		- 创建的 tuple 的名称只用于展示，返回的值才用于创建对象
	- 特殊函数
		- `__getitem__` 用于为类提供随机访问的能力
			- 对 choice、`[ ]` 访问等提供支持
		- `__contains__` 用于帮助 `in` 快速判断，否则就会顺序扫描一次来比较sure
		-