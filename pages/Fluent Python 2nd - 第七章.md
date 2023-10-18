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
	- 内置函数
		- len, time.strftime
	- 内置方法
	- 类方法
	- 类
	- 类实例
	- 生成器函数
		- 主题中使用 yield 的函数或方法