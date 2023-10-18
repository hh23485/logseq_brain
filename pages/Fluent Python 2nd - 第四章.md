tags:: [[Fluent Python 2nd@Books]]

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