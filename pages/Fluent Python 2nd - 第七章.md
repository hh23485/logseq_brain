tags:: [[Fluent Python 2nd@Books]]

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
	- ``` python
	  >>> fact = factorial
	  >>> fact
	  <function factorial at 0x...>
	  >>> fact(5)
	  120
	  >>> map(factorial, range(11))
	  <map object at 0x...>
	  >>> list(map(factorial, range(11)))
	  [1, 1, 2, 6, 24, 120, 720, 5040, 40320, 362880, 3628800]
	  
	  >>> [factorial(n) for n in range(6)]  
	  [1, 1, 2, 6, 24, 120]
	  >>> list(map(factorial, filter(lambda n: n % 2, range(6))))  
	  [1, 6, 120]
	  >>> [factorial(n) for n in range(6) if n % 2]  
	  [1, 6, 120]
	  >>>
	  ```
- lambda 用于创建一个匿名函数
	- python lambda 中不能包含复杂的内容，应该重构为 def 常规函数
	- 除了高阶函数之外，lambda 通常不使用，也要非常小心可读性
	- 一些建议
		- [“Functional Programming HOWTO” (fpy.li)](https://fpy.li/7-5)
- 可调用对象的九种类型
	- 用户定义的函数
	- 内置方法
		- len, time.strftime
	- 内置函数
	- 类函数
	- 类
	- 类实例
	- 生成器函数
		- 主题中使用 `yield` 的函数或方法
	- 本地协程方法
		- 使用 async def 函数或方法时，会返回一个协程对象
	- 异步生成器方法
		- async def
- 确认一个对象是否可调用的方法是，使用 `callable()` 来判断
	- ``` python
	  >>> abs, str, 'Ni!'
	  (<built-in function abs>, <class 'str'>, 'Ni!')
	  >>> [callable(obj) for obj in (abs, str, 'Ni!')]
	  [True, True, False]
	  
	  ```
- 如果不想要支持可变位置参数但仍然想要关键字参数，请在签名中单独放置 `*`
	- ``` python
	  >>> def f(a, *, b):
	  ...     return a, b
	  ...
	  >>> f(1, b=2)
	  (1, 2)
	  >>> f(1, 2)
	  Traceback (most recent call last):
	    File "<stdin>", line 1, in <module>
	  TypeError: f() takes 1 positional argument but 2 were given
	  
	  ```
- 使用 `/` 来定一个只允许按位置放置的函数参数列表，而不能使用关键字参数
	- ``` python
	  def divmod(a, b, /):
	      return (a // b, a % b)
	  
	  ```
	- 这样就不能使用 `divmod(a=10, b=4)` 而只能使用 `divmod(a, b)`
	- since 3.8
	- 但是在 `/` 之后的参数可以，例如
		- ``` python
		  def tag(name, /, *content, class_=None, **attrs):
		      ...
		  
		  ```
- 函数式编程
	- 使用 reduce 和 lambda 实现阶乘
		- ```python
		  from functools import reduce
		  def factorial(n): # 使用 reduce 对 range 生成的序列进行合并处理，合并使用 *
		    return reduce(lambda a, b: a*b, range(1, n+1))
		  ```
	- 或者使用 operator.mul
		- ``` python
		  from functools import reduce
		  from operator import mul
		  
		  def factorial(n):
		      return reduce(mul, range(1, n+1))
		  
		  ```
	- 类似的操作还有
		- `itemgetter([n])` 从序列中获取索引为 [n] 的元素
			- ``` python
			  >>> metro_data = [
			  ...     ('Tokyo', 'JP', 36.933, (35.689722, 139.691667)),
			  ...     ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)),
			  ...     ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)),
			  ...     ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)),
			  ...     ('São Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
			  ... ]
			  >>>
			  >>> from operator import itemgetter
			  >>> for city in sorted(metro_data, key=itemgetter(1)):
			  ...     print(city)
			  
			  ```
			- ``` python
			  >>> cc_name = itemgetter(1, 0)
			  >>> for city in metro_data:
			  ...     print(cc_name(city))
			  ...
			  ('JP', 'Tokyo')
			  ('IN', 'Delhi NCR')
			  ('MX', 'Mexico City')
			  ('US', 'New York-Newark')
			  ('BR', 'São Paulo')
			  >>>
			  
			  ```
		- `attrgetter` 类似，但用于获取对象的属性
			- ``` python
			  >>> from collections import namedtuple
			  >>> LatLon = namedtuple('LatLon', 'lat lon')  
			  >>> Metropolis = namedtuple('Metropolis', 'name cc pop coord')  
			  >>> metro_areas = [Metropolis(name, cc, pop, LatLon(lat, lon))  
			  ...     for name, cc, pop, (lat, lon) in metro_data]
			  >>> metro_areas[0]
			  Metropolis(name='Tokyo', cc='JP', pop=36.933, coord=LatLon(lat=35.689722,
			  lon=139.691667))
			  >>> metro_areas[0].coord.lat  
			  35.689722
			  >>> from operator import attrgetter
			  >>> name_lat = attrgetter('name', 'coord.lat')  
			  >>>
			  >>> for city in sorted(metro_areas, key=attrgetter('coord.lat')):  
			  ...     print(name_lat(city))  
			  ...
			  ('São Paulo', -23.547778)
			  ('Mexico City', 19.433333)
			  ('Delhi NCR', 28.613889)
			  ('Tokyo', 35.689722)
			  ('New York-Newark', 40.808611)
			  
			  ```
		- 可以使用 dir 来查看 operator 中定义的函数
			- ``` python
			  >>> [name for name in dir(operator) if not name.startswith('_')]
			  ['abs', 'add', 'and_', 'attrgetter', 'concat', 'contains',
			  'countOf', 'delitem', 'eq', 'floordiv', 'ge', 'getitem', 'gt',
			  'iadd', 'iand', 'iconcat', 'ifloordiv', 'ilshift', 'imatmul',
			  'imod', 'imul', 'index', 'indexOf', 'inv', 'invert', 'ior',
			  'ipow', 'irshift', 'is_', 'is_not', 'isub', 'itemgetter',
			  'itruediv', 'ixor', 'le', 'length_hint', 'lshift', 'lt', 'matmul',
			  'methodcaller', 'mod', 'mul', 'ne', 'neg', 'not_', 'or_', 'pos',
			  'pow', 'rshift', 'setitem', 'sub', 'truediv', 'truth', 'xor']
			  
			  ```
	- operator.methodcaller
		- 方法调用
			- ``` python
			  >>> from operator import methodcaller
			  >>> s = 'The time has come'
			  >>> upcase = methodcaller('upper')
			  >>> upcase(s)
			  'THE TIME HAS COME'
			  
			  ```
		- 参数绑定
			- ``` python
			  >>> hyphenate = methodcaller('replace', ' ', '-')
			  >>> hyphenate(s)
			  'The-time-has-come'
			  
			  ```
	- functools.partial
		- 冻结参数
			- ``` python
			  >>> from operator import mul
			  >>> from functools import partial
			  >>> triple = partial(mul, 3)  
			  >>> triple(7)  
			  21
			  >>> list(map(triple, range(1, 10)))  
			  [3, 6, 9, 12, 15, 18, 21, 24, 27]
			  
			  ```
			- 除了按照位置，也可以按照关键字
				- ``` python
				  >>> from tagger import tag
				  >>> tag
				  <function tag at 0x10206d1e0>  
				  >>> from functools import partial
				  >>> picture = partial(tag, 'img', class_='pic-frame')  
				  >>> picture(src='wumpus.jpeg')
				  '<img class="pic-frame" src="wumpus.jpeg" />'  
				  >>> picture
				  functools.partial(<function tag at 0x10206d1e0>, 'img', class_='pic-frame')  
				  >>> picture.func  
				  <function tag at 0x10206d1e0>
				  >>> picture.args
				  ('img',)
				  >>> picture.keywords
				  {'class_': 'pic-frame'}
				  
				  ```
- 进一步阅读
	- [PEP 3102—Keyword-Only Arguments (fpy.li)](https://fpy.li/pep3102)
	- [“Python: Why is functools.partial necessary?” (fpy.li)](https://fpy.li/7-12)
	- Python 是一种函数式语言嘛？
		- [slides (fpy.li)](https://fpy.li/7-13)
		- [video (fpy.li)](https://fpy.li/7-14)
		- #+BEGIN_QUOTE
		  What else to make of a language like Python, Ruby, or Perl? Their designers have no patience for the niceties of these Linnaean hierarchies; they borrow features as they wish, creating mélanges that utterly defy characterization.
		  还有什么可以对像Python、Ruby或Perl这样的语言做出解释呢？它们的设计者对这些分类学的细节毫不耐烦；他们随心所欲地借用特性，创造出完全无法归类的混合体。
		  #+END_QUOTE
		- [“Origins of Python’s ‘Functional’ Features”](https://fpy.li/7-1)
		- 大量嵌套的匿名函数会使调试和错误处理变得困难。Python中的异步编程更加结构化，可能是因为有限的语法防止了滥用，并强制采用更明确的方法。Promises、futures和deferreds是现代异步API中使用的概念。它们与协程一起提供了一种摆脱所谓的“回调地狱”的方法。我承诺将来会写更多关于异步编程的内容，但这个主题必须推迟到[第21章](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch21.html#async_ch)
	- TODO [“Flexible Object Creation with __new__” (oreilly.com)](https://learning.oreilly.com/library/view/fluent-python-2nd/9781492056348/ch22.html#flexible_new_sec)
	- functools.py 的源代码显示， functools.partial 是用 C 实现的，并且默认情况下会被使用。如果不可用，则自 Python 3.4 起提供了一个纯 Python 实现的 partial 。
		- [source code (fpy.li)](https://fpy.li/7-9)
-