tags:: [[JavaScript]], [[React]]

- 全称是 [[JavaScript]] XML
- React 定义的一种类似于 XML 的 JS 扩展语法: JS + XML
- 本质是 `React.createElement(component, props, ...children)` 方法的语法糖
- 作用是用来简化创建虚拟 Dom
	- 写法: `var element = <h1>Hello JSX!</h1>`
		- 不是字符串也不是标签
		- 是一个 JS 对象
	- 标签名可以为任意 HTML 标签或者其他标签
- 语法规则 #.ol
	- 定义 DOM 时不要写引号
	- 使用 `{}` 混用 JS 表达式
		- ``` html
		  <script type="text/babel">
		      let id = "virtual_id"
		      const vdom = <h1 id={id}>Hello, world!</h1>;
		      ReactDOM.render(vdom, document.getElementById('test'));
		  </script>
		  ```
	- 使用 `className` 来添加原 html 中的 `class` 样式类名
	- 内联样式使用
	- JSX 中只能有一个根标签
	- 标签必须闭合
	- 标签首字母如果是小写，就换转换成 html 中同名元素
	  id:: 6427dbd5-fb0a-4de1-bfad-7316d8dea0fd
		- 若无同名元素，则报错
-