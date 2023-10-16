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
	- 切片也用作 `list` 的操作控制
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
	- ((652a5a67-68b2-4c96-84d2-c5738766f844)) 可以传入一个 key
		- key 可以执行用于排序的元素，例如使用 key = len 或者 key=str.lower 来影响元素的排序
			- ``` python
			  >>> fruits = ['grape', 'raspberry', 'apple', 'banana']
			  >>> sorted(fruits)
			  ['apple', 'banana', 'grape', 'raspberry']  1
			  >>> fruits
			  ['grape', 'raspberry', 'apple', 'banana']  2
			  >>> sorted(fruits, reverse=True)
			  ['raspberry', 'grape', 'banana', 'apple']  3
			  >>> sorted(fruits, key=len)
			  ['grape', 'apple', 'banana', 'raspberry']  4
			  >>> sorted(fruits, key=len, reverse=True)
			  ['raspberry', 'banana', 'grape', 'apple']  5
			  >>> fruits
			  ['grape', 'raspberry', 'apple', 'banana']  6
			  >>> fruits.sort()                          7
			  >>> fruits
			  ['apple', 'banana', 'grape', 'raspberry']  8
			  
			  ```
		- python 使用的排序算法是 [[Timsort]]，是一种自适应算法，根据数据的有序程度切换插入排序和归并的排序策略
	- 对于只包含数字的列表，使用 `array.array` 的效率会更高
		- 支持所有的可变序列操作 `.pop`, `.insert`, `.extend`
		- 创建时候需要提供一个类型码来告诉 python 如何存储数组中每个项的底层 C 类型
			- ``` python
			  >>> from array import array  1
			  >>> from random import random
			  >>> floats = array('d', (random() for i in range(10**7)))  2    #设置为 d, double
			  >>> floats[-1]  3
			  0.07802343889111107
			  >>> fp = open('floats.bin', 'wb')
			  >>> floats.tofile(fp)  4
			  >>> fp.close()  # 存储大量浮点数到文件
			  
			  >>> floats2 = array('d')  5
			  >>> fp = open('floats.bin', 'rb')
			  >>> floats2.fromfile(fp, 10**7)  6 #还原大量浮点数
			  >>> fp.close()
			  
			  >>> floats2[-1]  7
			  0.07802343889111107
			  >>> floats2 == floats  8
			  True
			  
			  ```
		- 和 list 相比还有一些特别地方
			- 支持 s.byteswap()，对数组中所有的 item 进行字节交换以转换字节序
			- 支持 s.copy()
			- s.__deepcopy__() 对 copy.deepcopy 进行了优化
			- 支持 s.fromlist(l) 来从列表中添加
			- s.itemsize 获取每个数组项的字节长度
			- 不支持 s.sort()
				- 需要使用 a = array.array(a.typecode, sorted(a)) 重新构造一个数组
			- s.typecode 获取标识 item 的 C 类型
	- memoryview
		- 一共钟祥内存序列类型
		- 处理数组的切片而无需复制字节，受到了 [[NumPy]] 的启发
		- ``` python
		  >>> from array import array
		  >>> octets = array('B', range(6))
		  
		  # 从 array 构造了 memoryview
		  >>> m1 = memoryview(octets)
		  
		  # 转换为 list
		  >>> m1.tolist()
		  [0, 1, 2, 3, 4, 5]
		  
		  # 转换格式，但没有复制字节
		  >>> m2 = m1.cast('B', [2, 3])
		  >>> m2.tolist()
		  [[0, 1, 2], [3, 4, 5]]
		  >>> m3 = m1.cast('B', [3, 2])
		  >>> m3.tolist()
		  [[0, 1], [2, 3], [4, 5]]
		  
		  # 对 memoryview 的修改，会修改到源数据
		  >>> m2[1,1] = 22
		  >>> m3[1,1] = 33
		  >>> octets  7
		  array('B', [0, 1, 2, 33, 22, 5])
		  
		  ```
	- 对于高级复杂的数据处理要求，可以使用 [[NumPy]]
		- ``` python
		  >>> from array import array
		  >>> octets = array('B', range(6))  1
		  >>> m1 = memoryview(octets)  2
		  >>> m1.tolist()
		  [0, 1, 2, 3, 4, 5]
		  >>> m2 = m1.cast('B', [2, 3])  3
		  >>> m2.tolist()
		  [[0, 1, 2], [3, 4, 5]]
		  >>> m3 = m1.cast('B', [3, 2])  4
		  >>> m3.tolist()
		  [[0, 1], [2, 3], [4, 5]]
		  >>> m2[1,1] = 22  5
		  >>> m3[1,1] = 33  6
		  >>> octets  7
		  array('B', [0, 1, 2, 33, 22, 5])
		  
		  ```
		- 也同样支持从文件加载、保存和操作
			- ``` python
			  >>> import numpy
			  >>> floats = numpy.loadtxt('floats-10M-lines.txt') #加载数据
			  >>> floats[-3:]
			  array([ 3016362.69195522,   535281.10514262,  4566560.44373946])
			  >>> floats *= .5 #矩阵操作
			  >>> floats[-3:]
			  array([ 1508181.34597761,   267640.55257131,  2283280.22186973]) #逆向操作
			  
			  >>> from time import perf_counter as pc
			  >>> t0 = pc(); floats /= 3; pc() - t0    #计算时间
			  0.03690556302899495
			  
			  >>> numpy.save('floats-10M', floats)    #保存到文件
			  >>> floats2 = numpy.load('floats-10M.npy', 'r+')
			  >>> floats2 *= 6
			  >>> floats2[-3:]
			  memmap([ 3016362.69195522,   535281.10514262,  4566560.44373946])
			  
			  ```
	- deque
		- 双向队列，collections.deque 用来创建一个**线程安全**的双端队列
		- 可以设置为有界
			- ``` python
			  >>> from collections import deque
			  >>> dq = deque(range(10), maxlen=10)
			  >>> dq
			  deque([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
			  
			  >>> dq.rotate(3) #旋转
			  >>> dq
			  deque([7, 8, 9, 0, 1, 2, 3, 4, 5, 6], maxlen=10)
			  
			  >>> dq.rotate(-4)  #逆转4个
			  >>> dq
			  deque([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], maxlen=10)
			  
			  >>> dq.appendleft(-1)  #从左边添加
			  >>> dq
			  deque([-1, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
			  
			  >>> dq.extend([11, 22, 33])  #从右边添加
			  >>> dq
			  deque([3, 4, 5, 6, 7, 8, 9, 11, 22, 33], maxlen=10)
			  
			  >>> dq.extendleft([10, 20, 30, 40])  #按顺序从左边添加
			  >>> dq
			  deque([40, 30, 20, 10, 3, 4, 5, 6, 7, 8], maxlen=10)
			  
			  ```
			- `maxlen` 设置了一个上界
			- 已满 deque 中，继续往下塞，会导致丢弃另一端的 item
		- Python 标准库包实现了其他队列
			- queue
			- multiprocessing
			- asyncio
			- heapq
	- 扩展阅读
	  tags:: 扩展阅读
		- NumPy 的书籍
			- [From Python to NumPy (fpy.li)](https://fpy.li/2-31)
			- [Python Data Science Handbook (fpy.li)](https://fpy.li/2-29)
			- [Python for Data Analysis (fpy.li)](https://fpy.li/2-30)
		- memoryview
			- [“Less copies in Python with the buffer protocol and memoryviews” (fpy.li)](https://fpy.li/2-28)
		- 官方的排序指南 [“Sorting HOW TO” (fpy.li)](https://fpy.li/2-22)
- 第三章
	- 字典
		- dict 的构造可以从任何键值结构创建，只要使用 `{ }`
			- 推导
				- ``` python
				  >>> dial_codes = [
				  ...     (880, 'Bangladesh'),
				  ...     (55,  'Brazil'),
				  ...     (86,  'China'),
				  ...     (91,  'India'),
				  ...     (62,  'Indonesia'),
				  ...     (81,  'Japan'),
				  ...     (234, 'Nigeria'),
				  ...     (92,  'Pakistan'),
				  ...     (7,   'Russia'),
				  ...     (1,   'United States'),
				  ... ]
				  >>> country_dial = {country: code for code, country in dial_codes}
				  
				  ```
			- 解包映射
				- ``` python
				  >>> def dump(**kwargs):
				  ...     return kwargs
				  ...
				  >>> dump(**{'x': 1}, y=2, **{'z': 3})
				  {'x': 1, 'y': 2, 'z': 3}
				  
				  ```
			- 使用 `|` 或者 `|=` 合并两个 dict
				- ``` python
				  >>> d1 = {'a': 1, 'b': 3}
				  >>> d2 = {'a': 2, 'b': 4, 'c': 6}
				  >>> d1 | d2
				  {'a': 2, 'b': 4, 'c': 6}
				  
				  
				  >>> d1
				  {'a': 1, 'b': 3}
				  >>> d1 |= d2
				  >>> d1
				  {'a': 2, 'b': 4, 'c': 6}
				  
				  ```
		- 字典也可以进行模式匹配和映射（匹配任何 `collections.abc.Mapping`)
			- 例如从某种半结构数据中方便的提取数据和匹配
				- ``` python
				  def get_creators(record: dict) -> list:
				      match record:
				          case {'type': 'book', 'api': 2, 'authors': [*names]}:
				              return names
				          case {'type': 'book', 'api': 1, 'author': name}:
				              return [name]
				          case {'type': 'book'}:
				              raise ValueError(f"Invalid 'book' record: {record!r}")
				          case {'type': 'movie', 'director': name}:
				              return [name]
				          case _:
				              raise ValueError(f'Invalid record: {record!r}')
				  
				  ```
			- 也可以使用 **extra 来收集额外的键值对
				- ``` python
				  >>> food = dict(category='ice cream', flavor='vanilla', cost=199)
				  >>> match food:
				  ...     case {'category': 'ice cream', **details}:
				  ...         print(f'Ice cream details: {details}')
				  ...
				  Ice cream details: {'flavor': 'vanilla', 'cost': 199}
				  ```
	- 什么是可哈希的
		- #+BEGIN_QUOTE
		  如果一个对象具有在其生命周期内永远不会改变的哈希码（它需要一个 `__hash__()` 方法），并且可以与其他对象进行比较（它需要一个 `__eq__()` 方法），则该对象是可哈希的。具有相等比较的可哈希对象必须具有相同的哈希码
		  #+END_QUOTE
		- ``` python
		  >>> tt = (1, 2, (30, 40))
		  >>> hash(tt)
		  8027212646858338501
		  >>> tl = (1, 2, [30, 40])
		  >>> hash(tl)
		  Traceback (most recent call last):
		    File "<stdin>", line 1, in <module>
		  TypeError: unhashable type: 'list'
		  ```
	- `__missing__`
		- 这是一个特殊方法，用来在访问字典时处理不存在的 key
			- ![image.png](../assets/image_1697423167224_0.png)
			- 通过 override 形式能够覆盖对 `__getitem__` 的失败访问，但不覆盖 `__contains__`
				- 这个例子可以让数组里不论存放的 key 是字符串还是数字，都能够被正常的访问
				- ![image.png](../assets/image_1697423252380_0.png)
		- 该特殊方法在特定的实现类中的覆盖范围有一些差异
			- 对于 dict 子类如果只实现了 `__missing__`，意味着对下面两个方法进行了支持
				- `d[k]`
				- `__getitem__`
			- 对于 `collections.UserDict` 的子类，如果只实现了 `__missing__`，支持如下方法
				- `d[k]`
				- `d.get(k)`
			- 对于 `abc.Mapping` 子类中的逻辑完全取决于你是否在 `__getitem__` 中调用 `__missing__`
				- 如果不调用，则默认不会触发
				- 如果自己调用了，那么可以覆盖 `d[k]`, `d.get(k)`，`k in d`
			- `setdefault` 和 `update` 的行为也会受到影响
	- `defaultdict`
		- 是一个默认值的 dict 变体，如果这个
	- `collections.OrderedDict`
		- 自 3.6 版本开始，内置的 dict 也会保持键的顺序，所以使用 `OrderedDict` 的常见原因是
		- 带有一个 `move_to_end()` 方法可以调整顺序
		- 比 `dict` 更擅长重新排序，空间效率、插入性能都是次要的
	- `ChainMap`
		- 像是一个层次的 dict，可以按顺序将多个 dict 组织起来，在查询时按照顺序从第一个 dict 开始查找
		- ``` python
		  >>> d1 = dict(a=1, b=3)
		  >>> d2 = dict(a=2, b=4, c=6)
		  >>> from collections import ChainMap
		  >>> chain = ChainMap(d1, d2)
		  >>> chain['a']
		  1
		  >>> chain['c']
		  6
		  ```
		- ``` python
		  >>> chain['c'] = -1
		  >>> d1
		  {'a': 1, 'b': 3, 'c': -1}
		  >>> d2
		  {'a': 2, 'b': 4, 'c': 6}
		  ```
		- 对于环境变量的、上下文的设置非常有效
			- ``` python
			  import builtins
			  pylookup = ChainMap(locals(), globals(), vars(builtins))
			  ```
	- `collections.Counter`
		- ``` python
		  >>> ct = collections.Counter('abracadabra')
		  >>> ct
		  Counter({'a': 5, 'b': 2, 'r': 2, 'c': 1, 'd': 1})
		  >>> ct.update('aaaaazzz')
		  >>> ct
		  Counter({'a': 10, 'z': 3, 'b': 2, 'r': 2, 'c': 1, 'd': 1})
		  >>> ct.most_common(3)
		  [('a', 10), ('z', 3), ('b', 2)]
		  ```
		- 提供了一些有意思的接口
			- most_common 来获取 top n 的元素
			- total 所有元素总计数
			- elements 获取所有的元素，返回的是一个迭代类型，可以用于排序或者转换成 list
			- 也可以使用  + - | 来合并、删除两个 dict
				- ``` python
				  c = Counter(a=3, b=1)
				  **>>> **d = Counter(a=1, b=2)
				  **>>> **c + d                       *# add two counters together:  c[x] + d[x]*
				  Counter({'a': 4, 'b': 3})
				  **>>> **c - d                       *# subtract (keeping only positive counts)*
				  Counter({'a': 2})
				  **>>> **c & d                       *# intersection:  min(c[x], d[x])*
				  Counter({'a': 1, 'b': 1})
				  **>>> **c | d                       *# union:  max(c[x], d[x])*
				  Counter({'a': 3, 'b': 2})
				  ```
			- 如果想要针对非单个字母的，需要手动添加
				- ``` python
				  c = Counter({'red': 4, 'blue': 2})      # a new counter from a mapping
				  c = Counter(cats=4, dogs=8)             # a new counter from keyword args
				  ```
	- 需要实现一个 dict 子类的时候，使用 `UserDict` 而不是直接继承自 `dict`
		- UserDict 并不是 dict 子类，而是使用组合的方式，在内部持有了一个 dict 实例
		- 这样可以在必要的时候才重写一些函数，且重写的时候仍然可以依赖 dict 的实现
			- ![image.png](../assets/image_1697441608170_0.png)
			-
-
