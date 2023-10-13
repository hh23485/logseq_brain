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
			- 数学运算
				- 各种基础运算都有对应的特殊方法来实现
				- 如果第一个操作数的响应特殊方法无法使用，就会在第二个操作数上调用一个反向操作的特殊方法
	- 进一步阅读
		- [“Data Model” chapter (fpy.li)](https://fpy.li/dtmodel)
		- [Python in a Nutshell, 3rd ed. (fpy.li)](https://fpy.li/pynut3) 对数据模型的访问机制的描述
		- [The Art of the Metaobject Protocol (mit.edu)](https://mitpress.mit.edu/books/art-metaobject-protocol) 解释了元对象协议的概念，其中举了 python 数据模型的例子
			- 书作者也是 AspectJ 的作者
			- 元对象是构建语言核心结构的 API，如果足够灵活就可以扩展出新的编程范式
- 第二章
	- 序列分类
		- 按结构
			- 容器序列
				- 可以容纳不同类型的项目
			- 扁平序列
				- str, bytes, array.array
			- ![image.png](../assets/image_1697004762789_0.png)
	- 可变性
		- 可变
			- list, bytearray, array.array, collections.deque
		- 不可变
			- tuple, str, bytes
		- ![image.png](../assets/image_1697004925620_0.png)
	- python 中每个对象都有一个带元数据的头部，以 float 为例
		- ob_refcnt: 引用计数
		- ob_type: 指向对象类型的指针
		- ob_fval: 一个包含 float 值的 C double
	- 列表推导器
		- ``` python
		  symbols = '$¢£¥€¤'
		  codes = [ord(symbol) for symbol in symbols]
		  
		  ```
			- symbol 这里创建的变量是一个局部变量，不会和外面冲突
			- 但如果是用 `:=` 来分配的话，就可以在外界访问
				- ``` python
				  >>> codes = [last := ord(c) for c in x]
				  >>> last  2
				  
				  ```
		- 推导器可以用于多个循环
			- ``` python
			  >>> tshirts = [(color, size) for color in colors for size in sizes]  #+BEGIN_EXPORT hiccup
			  >>> tshirts
			  [('black', 'S'), ('black', 'M'), ('black', 'L'), ('white', 'S'),
			   ('white', 'M'), ('white', 'L')]
			  ```
		- 但所有的数据都是一次性生成，但好在比 map/filter 更快
	- 生成器表达式
		- 生成器构造的是一个迭代器，可以不断的产出新的元素，而不是一次性生成所有
		- 和列表推导器的差别是，不使用方括号而使用圆括号
			- ``` python
			  >>> colors = ['black', 'white']
			  >>> sizes = ['S', 'M', 'L']
			  >>> for tshirt in (f'{c} {s}' for c in colors for s in sizes):  
			  ...     print(tshirt)
			  ```
	- Tuple 是一个不可变对象，但是其引用的对象可能是可变的
		- 在 python 中如果想要知道一个对象是不是完全不可变，值是不是确定的，可以使用如下方法
			- ``` python
			  >>> def fixed(o):
			  ...     try:
			  ...         hash(o)
			  ...     except TypeError:
			  ...         return False
			  ...     return True
			  ...
			  >>> tf = (10, 'alpha', (1, 2))
			  >>> tm = (10, 'alpha', [1, 2])
			  >>> fixed(tf)
			  True
			  >>> fixed(tm)
			  False
			  ```
			- hash 对于非固定不变的对象，就会抛异常
	- 使用 * 解包
		- ``` python
		  >>> a, b, *rest = range(5)
		  >>> a, b, rest
		  (0, 1, [2, 3, 4])
		  >>> a, b, *rest = range(3)
		  >>> a, b, rest
		  (0, 1, [2])
		  >>> a, b, *rest = range(2)
		  >>> a, b, rest
		  (0, 1, [])
		  
		  >>> a, *body, c, d = range(5)
		  >>> a, body, c, d
		  (0, [1, 2], 3, 4)
		  
		  >> def fun(a, b, c, d, *rest):
		  ...     return a, b, c, d, rest
		  ...
		  >>> fun(*[1, 2], 3, *range(4, 7))
		  (1, 2, 3, 4, (5, 6))
		  
		  ```
	- 嵌套解包
		- `[record] = query_returning_single_row()` 用于 返回值为 list 但只有一个元素
		- `[[field]] = query_returning_single_row_with_single_field()` 用于 返回值为 list，但只有一个元素，且元素只有一个字段
	- 模式匹配中解包
		- ``` python
		      def handle_command(self, message):
		          match message:  1
		              case ['BEEPER', frequency, times]:
		                  self.beep(times, frequency)
		              case ['NECK', angle]:
		                  self.rotate_neck(angle)
		              case ['LED', ident, intensity]:
		                  self.leds[ident].set_brightness(ident, intensity)
		              case ['LED', ident, red, green, blue]:
		                  self.leds[ident].set_color(ident, red, green, blue)
		              case _:
		                  raise InvalidCommand(message)
		  ```
			- 第一个元素都是字符串，然后，其他元素会被逐步放置
		- 另外一个例子
			- ``` python
			  metro_areas = [
			      ('Tokyo', 'JP', 36.933, (35.689722, 139.691667)),
			      ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)),
			      ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)),
			      ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)),
			      ('São Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
			  ]
			  
			  def main():
			      print(f'{"":15} | {"latitude":>9} | {"longitude":>9}')
			      for record in metro_areas:
			          match record:  
			              case [name, _, _, (lat, lon)] if lon <= 0:  
			                  print(f'{name:15} | {lat:9.4f} | {lon:9.4f}')
			  
			  ```
		- 被匹配的可以是元组或者列表，可嵌套
		- 规则和普通的解包是相同的，也可以使用 `*`
		- 也可以自己设置格式 `case [str(name), *_, (float(lat), float(lon))]`
		- `_` 可以匹配任何变量，`*_` 可以匹配任意数量的项目，而不绑定到任何变量
	- 切片也用作 list 的操作控制
		- ``` python
		  >>> l = list(range(10))
		  >>> l
		  [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
		  >>> l[2:5] = [20, 30]
		  >>> l
		  [0, 1, 20, 30, 5, 6, 7, 8, 9]
		  >>> del l[5:7]
		  >>> l
		  [0, 1, 20, 30, 5, 8, 9]
		  >>> l[3::2] = [11, 22]
		  >>> l
		  [0, 1, 20, 11, 5, 22, 9]
		  >>> l[2:5] = 100  1
		  Traceback (most recent call last):
		    File "<stdin>", line 1, in <module>
		  TypeError: can only assign an iterable
		  >>> l[2:5] = [100]
		  >>> l
		  [0, 1, 100, 22, 9]
		  ```
	- 对序列使用 + 和 *
		- + 可以用于拼接
		- * 可以用于重复序列中的值
			- ``` python
			  >>> l = [1, 2, 3]
			  >>> l * 5
			  [1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3, 1, 2, 3]
			  >>> 5 * 'abcd'
			  'abcdabcdabcdabcdabcd'
			  
			  ```
	- 自增操作
		- 对于 python 自带的可变序列，都实现了 `__iadd__`
		-
	- 切片
		- 切片实际上是构造了一个 slice 对象，并传递给容器的 __getitem__ 方法，来够造一个新的容器
		- 也可以如下操作
			- ``` python
			  >>> invoice = """
			  ... 0.....6.................................40........52...55........
			  ... 1909  Pimoroni PiBrella                     $17.50    3    $52.50
			  ... 1489  6mm Tactile Switch x20                 $4.95    2     $9.90
			  ... 1510  Panavise Jr. - PV-201                 $28.00    1    $28.00
			  ... 1601  PiTFT Mini Kit 320x240                $34.95    1    $34.95
			  ... """
			  >>> SKU = slice(0, 6)
			  >>> DESCRIPTION = slice(6, 40)
			  >>> UNIT_PRICE = slice(40, 52)
			  >>> QUANTITY =  slice(52, 55)
			  >>> ITEM_TOTAL = slice(55, None)
			  >>> line_items = invoice.split('\n')[2:]
			  >>> for item in line_items:
			  ...     print(item[UNIT_PRICE], item[DESCRIPTION])
			  ...
			      $17.50   Pimoroni PiBrella
			       $4.95   6mm Tactile Switch x20
			      $28.00   Panavise Jr. - PV-201
			      $34.95   PiTFT Mini Kit 320x240
			  
			  ```
		- 当切片在等号左边的时候，事实上是对容器原地的修改
			- ``` python
			  >>> l = list(range(10))
			  >>> l
			  [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
			  >>> l[2:5] = [20, 30]
			  >>> l
			  [0, 1, 20, 30, 5, 6, 7, 8, 9]
			  >>> del l[5:7]
			  >>> l
			  [0, 1, 20, 30, 5, 8, 9]
			  >>> l[3::2] = [11, 22]
			  >>> l
			  [0, 1, 20, 11, 5, 22, 9]
			  
			  ```
	-
