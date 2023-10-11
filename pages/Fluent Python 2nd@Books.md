tags:: [[Python]], [[Books]]

- 第一章
	- namedtuple
		- 创建的 tuple 的名称只用于展示，返回的值才用于创建对象
	- 特殊函数通常用于被各种内部逻辑隐式调用
		- `__getitem__` 用于为类提供随机访问的能力
			- 对迭代、choice、`[ ]`访问、排序等提供支持
			- ![UML class diagram with all superclasses and some subclasses of `abc.Collection`](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781492056348/files/assets/flpy_0102.png)
				- `dict` 自 3.7 被认为是有序的，但只代表保留了插入顺序，不代表你可以排序
				- python 中对于容器的这种继承关系，并不需要存在真实的继承，而只需要存在对应的特殊函数即可
		- `__contains__` 用于帮助 `in` 快速判断，否则就会顺序扫描一次来比较sure
		- `__len__` 提供 len 关键字的逻辑
		- 特殊函数有 80 多个
			- 功能性
				- col-w-1:: 234px
				  |  类别 | Method names |
				  | ---- | ---- | ---- | ---- |
				  | 字符串/字节表示 | `__repr__ __str__ __format__ __bytes__ __fspath__` |
				  |  转换为数字 | `__bool__ __complex__ __int__ __float__ __hash__ __index__` |
				  | 模仿集合 | `__len__ __getitem__ __setitem__ __delitem__ ``__contains__` |
				  |  迭代 | `__iter__ __aiter__ __next__ __anext__ __reversed__` |
				  | 可调用或协程执行 | `__call__ __await__` |
				  |  上下文管理 | `__enter__ __exit__ __aexit__ __aenter__` |
				  | 实例创建和销毁 | `__new__ __init__ __del__` |
				  |  属性管理 | `__getattr__ __getattribute__ __setattr__ __delattr__ __dir__` |
				  |  属性描述符 | `__get__ __set__ __delete__ __set_name__` |
				  |  抽象基类 | `__instancecheck__ __subclasscheck__` |
				  |  类元编程 | `__prepare__ __init_subclass__ __class_getitem__ __mro_entries__` |
			- 数学
				-