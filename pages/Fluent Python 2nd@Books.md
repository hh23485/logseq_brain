tags:: [[Python]], [[Books]]

- [[Fluent Python 2nd - 第一章]]
  collapsed:: true
- [[Fluent Python 2nd - 第二章]]
  collapsed:: true
- [[Fluent Python 2nd - 第三章]]
  collapsed:: true
- 第四章
  collapsed:: true
	- 获取当前环境相关的编码设置
		- ``` python
		  import locale
		  import sys
		  - expressions = """
		        locale.getpreferredencoding()
		        type(my_file)
		        my_file.encoding
		        sys.stdout.isatty()
		        sys.stdout.encoding
		        sys.stdin.isatty()
		        sys.stdin.encoding
		        sys.stderr.isatty()
		        sys.stderr.encoding
		        sys.getdefaultencoding()
		        sys.getfilesystemencoding()
		    """
		  - my_file = open('dummy', 'w')
		  - for expression in expressions.split():
		    value = eval(expression)
		    print(f'{expression:>30} -> {value!r}')
		  ```
	- Windows 上的执行时的编码和 stdout 的编码会是完全不同的值，很奇妙
		- ```
		  Z:\>python default_encodings.py > encodings.log # 会得到和上面不同的结果
		  ```
	- 中间省略了，没看
	- 正则表达式中的 str 和 bytes
		- 正则表达式如果对于输入也使用 bytes，那么 regex 也可以使用 bytes 来编译
		- regex 有参数 `re.ASCII` 来限制`\w`, `\W`, `\b`, `\B`, `\d`, `\D`, `\s`, 和`\S` 等参数只匹配 `ASCII`
- 第五章
  collapsed:: true
	- Data Class Builder
		- 构建类的简单方式，这些类只是一些数据字段的集合，不具备其他功能
			- 相比于手动构造一个类，继承自 object 的一些默认实现的方法并不是很有用
				- `__repr__` 没什么用
				- `__eq__` 只会比较 id
				- 等等
				- ``` python
				  >>> from coordinates import Coordinate
				  >>> moscow = Coordinate(55.76, 37.62)
				  >>> moscow
				  <coordinates.Coordinate object at 0x107142f10>  1
				  >>> location = Coordinate(55.76, 37.62)
				  >>> location == moscow  2
				  False
				  
				  ```
		- 三种
			- `collections.namedtuple`
				- ``` python
				  >>> from collections import namedtuple
				  >>> Coordinate = namedtuple('Coordinate', 'lat lon')
				  >>> issubclass(Coordinate, tuple)
				  True
				  >>> moscow = Coordinate(55.756, 37.617) #可以 print
				  >>> moscow
				  Coordinate(lat=55.756, lon=37.617)  
				  >>> moscow == Coordinate(lat=55.756, lon=37.617)  #可以直接比较
				  True
				  ```
			- `typing.NamedTuple`
				- ``` python
				  >>> import typing
				  >>> Coordinate = typing.NamedTuple('Coordinate',
				  ...     [('lat', float), ('lon', float)]) # 提供了相同的功能
				  >>> issubclass(Coordinate, tuple)
				  True
				  >>> typing.get_type_hints(Coordinate)
				  {'lat': <class 'float'>, 'lon': <class 'float'>}
				  ```
				- 也可以在构造类时使用
					- ``` python
					  from typing import NamedTuple
					  
					  class Coordinate(NamedTuple):
					      lat: float
					      lon: float
					  
					      def __str__(self):
					          ns = 'N' if self.lat >= 0 else 'S'
					          we = 'E' if self.lon >= 0 else 'W'
					          return f'{abs(self.lat):.1f}°{ns}, {abs(self.lon):.1f}°{we}'
					  ```
					- 但 NamedTuple 并不是超类
			- `@dataclasses.dataclass`
				- ``` python
				  from dataclasses import dataclass
				  
				  @dataclass(frozen=True)
				  class Coordinate:
				      lat: float
				      lon: float
				  
				      def __str__(self):
				          ns = 'N' if self.lat >= 0 else 'S'
				          we = 'E' if self.lon >= 0 else 'W'
				          return f'{abs(self.lat):.1f}°{ns}, {abs(self.lon):.1f}°{we}'
				  
				  ```
		- 一些操作和特性
			- ||  命名元组 |  命名元组 |  数据类 |
			  | ---- | ---- | ---- |
			  |  可变实例（指的是在类构造时使用） | NO | NO | YES |
			  |  类语句语法 | NO | YES | YES |
			  |  构建字典 | x._asdict() | x._asdict() | dataclasses.asdict(x) |
			  |  获取字段名称 | x._fields | x._fields | [f.name for f in dataclasses.fields(x)] |
			  |  获取默认值 | x._field_defaults | x._field_defaults | [f.default for f in dataclasses.fields(x)] |
			  |  获取字段类型 | N/A | x.__annotations__ | x.__annotations__ |
			  | 新实例与更改 | x._replace(…) | x._replace(…) | dataclasses.replace(x, …) |
			  |  在运行时创建新的类 | namedtuple(…) | NamedTuple(…) | dataclasses.make_dataclass(…) |
		- namedtuple 支持设置最右边的 N 个元素的默认值
			- ``` python
			  >>> Coordinate = namedtuple('Coordinate', 'lat lon reference', defaults=['WGS84'])
			  >>> Coordinate(0, 0)
			  Coordinate(lat=0, lon=0, reference='WGS84')
			  >>> Coordinate._field_defaults
			  {'reference': 'WGS84'}
			  
			  ```
		- namedtuple 的可以添加成员方法，但传递的是外部函数，参数需要模拟 self，因此传递一个相同类型的参数
			- ``` python
			  >>> Card.suit_values = dict(spades=3, hearts=2, diamonds=1, clubs=0)  
			  >>> def spades_high(card):                                            
			  ...     rank_value = FrenchDeck.ranks.index(card.rank)
			  ...     suit_value = card.suit_values[card.suit]
			  ...     return rank_value * len(card.suit_values) + suit_value
			  ...
			  >>> Card.overall_rank = spades_high                                   
			  >>> lowest_card = Card('2', 'clubs')
			  >>> highest_card = Card('A', 'spades')
			  >>> lowest_card.overall_rank()                                        
			  0
			  >>> highest_card.overall_rank()
			  51
			  
			  ```
		- 类型提示
			- Python 类型提示不强制，如果需要查看效果，必须运行特定的工具，例如 `mypy`
			- 可以通过 __annotations__ 里获取类型提示信息
				- ``` python
				  class DemoPlainClass:
				      a: int           
				      b: float = 1.1   
				      c = 'spam'       
				      
				  >>> from demo_plain import DemoPlainClass
				  >>> DemoPlainClass.__annotations__
				  {'a': <class 'int'>, 'b': <class 'float'>}
				  
				  ```
			- 上面例子中的 `DemoPlainClass` class 的 `a` 在有值之前是不存在的
				- ``` python
				  >>> DemoPlainClass.a
				  Traceback (most recent call last):
				    File "<stdin>", line 1, in <module>
				  AttributeError: type object 'DemoPlainClass' has no attribute 'a'
				  >>> DemoPlainClass.b
				  1.1
				  >>> DemoPlainClass.c
				  'spam'
				  
				  ```
			- 然而在 `typing.NamedTuple` 的基础上构建的类并不相通，即便字段没有值，也会存在
				- ``` python
				  import typing
				  
				  class DemoNTClass(typing.NamedTuple):
				      a: int           
				      b: float = 1.1   
				      c = 'spam'       
				  ```
				- ``` python
				  >>> from demo_nt import DemoNTClass
				  >>> DemoNTClass.__annotations__
				  {'a': <class 'int'>, 'b': <class 'float'>}
				  >>> DemoNTClass.a
				  <_collections._tuplegetter object at 0x101f0f940>
				  >>> DemoNTClass.b
				  <_collections._tuplegetter object at 0x101f0f8b0>
				  >>> DemoNTClass.c
				  'spam'
				  
				  ```
			- `@dataclass` 和 `class` 会比较像，但还会生成一个 `__doc__` 字段
				- ``` python
				  >>> from dataclasses import dataclass
				  >>>
				  >>> @dataclass
				  ... class DemoDataClass:
				  ...     a: int
				  ...     b: float = 1.1
				  ...     c = 'spam'
				  ...
				  >>> DemoDataClass
				  <class '__main__.DemoDataClass'>
				  >>> DemoDataClass.__doc__
				  'DemoDataClass(a: int, b: float = 1.1)'
				  
				  ```
	- 更多关于 @dataclass 装饰器
		- |  选项 |  意义 |  默认 |  注释 |
		  | ---- | ---- | ---- |
		  | `init` |  生成 `__init__` | `True` | 如果用户实现了 `__init__` ，则忽略。 |
		  | `repr` |  生成 `__repr__` | `True` | 如果用户实现了 `__repr__` ，则忽略。 |
		  | `eq` |  生成 `__eq__` | `True` | 如果用户实现了 `__eq__` ，则忽略。 |
		  | `order` | 生成 `__lt__` , `__le__` , `__gt__` , `__ge__` | `False` | 如果 `True` ，则在 `eq=False` 时引发异常，或者如果定义或继承了任何将生成的比较方法。 |
		  | `unsafe_hash` |  生成 `__hash__` | `False` | 复杂的语义和几个注意事项-请参阅：dataclass文档。 |
		  | `frozen` | 使实例“不可变” | `False` | 实例将相对安全，不容易发生意外更改，但并非真正不可变。|
		- `@dataclass` 不能使用可变默认值
			- ``` python
			  @dataclass
			  class ClubMember:
			      name: str
			      guests: list = []
			      
			  $ python3 club_wrong.py
			  Traceback (most recent call last):
			    File "club_wrong.py", line 4, in <module>
			      class ClubMember:
			    ...several lines omitted...
			  ValueError: mutable default <class 'list'> for field guests is not allowed:
			  use default_factory
			  
			  ```
			- 需要使用 `default_factory` 和 `field`
				- ``` python
				  from dataclasses import dataclass, field
				  
				  @dataclass
				  class ClubMember:
				      name: str
				      guests: list[str] = field(default_factory=list)
				  ```
		- `field` 接受的参数，用来控制生成的内容
			- |  选项 |  意义 |  默认 |
			  | ---- | ---- | ---- |
			  | `default` |  字段的默认值 | `_MISSING_TYPE`[a](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch05.html#idm46582453966752) |
			  | `default_factory` | 用于生成默认值的0参数函数 | `_MISSING_TYPE` |
			  | `init` | 在参数中包含字段 `__init__` | `True` |
			  | `repr` | 在 `__repr__` 中包含字段 | `True` |
			  | `compare` | 使用字段进行比较方法 `__eq__` ， `__lt__` 等。 | `True` |
			  | `hash` | 在计算中包含字段 `__hash__` | `None`[b](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch05.html#idm46582453951136) |
			  | `metadata` | 使用用户定义的数据进行映射；被 `@dataclass` 忽略 | `None` |
		- @dataclass 会自动调用 `__post_init__`
			- 用于在 `__init__` (单纯赋值) 之后，对放入的成员进行一些校验工作
			- ``` python
			  @dataclass
			  class HackerClubMember(ClubMember):                         
			      all_handles = set()                                     
			      handle: str = ''                                        
			  
			      def __post_init__(self):
			          cls = self.__class__                                
			          if self.handle == '':                               
			              self.handle = self.name.split()[0]
			          if self.handle in cls.all_handles:                  
			              msg = f'handle {self.handle!r} already exists.'
			              raise ValueError(msg)
			          cls.all_handles.add(self.handle)   
			  
			  ```
			- [在 @dataclass 中，所有具有类型标注的类变量都被视为实例级别的变量 (python.org)](https://docs.python.org/zh-cn/3/library/dataclasses.html)
				- 但这个设计没有办法通过 mypy，因为会认为缺少类型标注
				- 那么如果想要构造一个类变量且带标准，需要如下方法
					- ``` python
					  all_handles: ClassVar[set[str]] = set()
					  ```
		- @dataclass 与伪类型
			- 可能在构造 dataclass 时你希望传入一个对象，但并不想要它成为其中一个字段，你需要借助 `InitVar`
			- ``` python
			  @dataclass
			  class C:
			      i: int
			      j: int = None
			      database: InitVar[DatabaseType] = None
			  
			      def __post_init__(self, database):
			          if self.j is None and database is not None:
			              self.j = database.lookup('j')
			  
			  c = C(10, database=my_database)
			  
			  ```
			- 这个 database 并不会被视作一个字段，但必须要在构造函数中传入，你可以在 `__post_init__` 中访问
		- 使用 `self.__class__.__name__` 获得类名
		- 使用 fields(self.__class__) 来获得所有的字段序列
		- 使用 `getattr(obj, f.name)` 来获得字段的值
		- 类实例用作模式匹配
			- 按字段
				- ``` python
				  import typing
				  
				  class City(typing.NamedTuple):
				      continent: str
				      name: str
				      country: str
				  
				  
				  cities = [
				      City('Asia', 'Tokyo', 'JP'),
				      City('Asia', 'Delhi', 'IN'),
				      City('North America', 'Mexico City', 'MX'),
				      City('North America', 'New York', 'US'),
				      City('South America', 'São Paulo', 'BR'),
				  ]
				  
				  def match_asian_cities():
				      results = []
				      for city in cities:
				          match city:
				              case City(continent='Asia'):
				                  results.append(city)
				      return results
				  
				  ```
			- 按字段位置
				- ``` python
				  def match_asian_countries_pos():
				      results = []
				      for city in cities:
				          match city:
				              case City('Asia', _, country):
				                  results.append(country)
				      return results
				  
				  ```
				- 如果想要知道顺序，可以使用 `City.__match_args__`
		- 延伸阅读
			- [“Why not just use namedtuple?” (fpy.li)](https://fpy.li/5-18)
			- [“Why not just use typing.NamedTuple?” (fpy.li)](https://fpy.li/5-19)
			- [“Dataclasses: The code generator to end all code generators” (video) (fpy.li)](https://fpy.li/5-23)
			- [“Ultimate guide to data classes in Python 3.7” (fpy.li)](https://fpy.li/5-22)
- 第六章
  collapsed:: true
	- python 中的 is 是比较两个对象的 id 是否相同，而 == 比较的是两个对象所持有的值是否相同
		- object 默认实现的 `__eq__` 就是比较两个 id，所以会得到和 is 相同的结果
		- 通常领域对象都会重新实现 `__eq__`
		- ``` python
		  >>> t1 = (1, 2, [30, 40])  
		  >>> t2 = (1, 2, [30, 40])  
		  >>> t1 == t2  
		  True
		  >>> id(t1[-1])  
		  4302515784
		  >>> t1[-1].append(99)  
		  >>> t1
		  (1, 2, [30, 40, 99])
		  >>> id(t1[-1])  
		  4302515784
		  >>> t1 == t2  
		  False
		  
		  ```
	- copy 模块提供了 `copy()` 和 `deepcopy()`
		- ``` python
		  >>> import copy
		  >>> bus1 = Bus(['Alice', 'Bill', 'Claire', 'David'])
		  >>> bus2 = copy.copy(bus1)
		  >>> bus3 = copy.deepcopy(bus1)
		  >>> id(bus1), id(bus2), id(bus3)
		  (4301498296, 4301499416, 4301499752)  
		  >>> bus1.drop('Bill')
		  >>> bus2.passengers
		  ['Alice', 'Claire', 'David']          
		  >>> id(bus1.passengers), id(bus2.passengers), id(bus3.passengers)
		  (4302658568, 4302658568, 4302657800)  
		  >>> bus3.passengers
		  ['Alice', 'Bill', 'Claire', 'David']  
		  
		  ```
	- `deepcopy` 可以保证循环依赖也被正确的复制
		- 也可以通过实现 `__copy__()` 和 `__deepcopy__()` 来控制 copy 和 deepcopy
	- python 中默认值如果是可变类型，那么所有的实例使用默认值的会默认共享同一个，如果任何一个操作修改了，对于所有的对象就都可见了
		- 而不是每次都会新建一个
		- 你可以从 `dir(class.__init__)` 中看到默认值的状态
		- **因此通常，可变类型的默认值是 `None`**
	- del 删除的不是对象而是引用
	- 如何观察对象的结束
		- 可以使用 `weakref.finalize` 注册一个回调函数
			- ``` python
			  >>> import weakref
			  >>> s1 = {1, 2, 3}
			  >>> s2 = s1         
			  >>> def bye():      
			  ...     print('...like tears in the rain.')
			  ...
			  >>> ender = weakref.finalize(s1, bye)   #不会增加引用计数
			  >>> ender.alive  
			  True
			  >>> del s1
			  >>> ender.alive  
			  True
			  >>> s2 = 'spam'  
			  ...like tears in the rain.
			  >>> ender.alive
			  False
			  
			  ```
	- `tuple(t1)` 和 `t1[:]` 返回的都是 t1 同一对象的引用，而不会拷贝一个新的
		- ``` python
		  >>> t1 = (1, 2, 3)
		  >>> t2 = tuple(t1)
		  >>> t2 is t1  
		  True
		  >>> t3 = t1[:]
		  >>> t3 is t1  
		  True
		  
		  ```
		- `str`, `bytes`, `frozenset` 具有相同的行为，对于不可变对象的一种优化
			- 甚至 `frozenset.copy()` 返回的也是相同的对象的引用而不是一个副本
	- 延伸阅读
		- [“PyPy, Garbage Collection, and a Deadlock” (fpy.li)](https://fpy.li/6-7)
		- [Understanding Python’s Memory Model, Mutability, and Methods (fpy.li)](https://fpy.li/6-8)
		- [gc module documentation (fpy.li)](https://fpy.li/6-11)
		- [“Design of CPython’s Garbage Collector” (fpy.li)](https://fpy.li/6-12)
		- [PEP 442—Safe object finalization (fpy.li)](https://fpy.li/6-14)
		- [string interning (fpy.li)](https://fpy.li/6-15)
	- 其他
		- 对于需要销毁和关闭的对象，尽量使用 with，而不是依赖垃圾回收
		- ![image.png](../assets/image_1697604404316_0.png).
		-
- 第七章
	- python 中的 function 是一等公民
		- ``` python
		  >>> def factorial(n):  
		  ...     """returns n!"""
		  ...     return 1 if n < 2 else n * factorial(n - 1)
		  ...
		  >>> factorial(42)
		  1405006117752879898543142606244511569936384000000000
		  >>> factorial.__doc__  
		  'returns n!'
		  >>> type(factorial)  
		  <class 'function'>
		  ```
	- 让函数式编程成为可能 [functional programming (fpy.li)](https://fpy.li/7-4)
	-
-