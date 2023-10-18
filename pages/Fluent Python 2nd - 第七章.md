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
-