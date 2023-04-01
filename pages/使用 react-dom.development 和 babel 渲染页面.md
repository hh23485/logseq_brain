tags:: React

- 最简使用 React JS 的方法
	- 添加如下依赖
		- react.development.js
			- 引入 react 核心库
		- react-dom.development.js
			- 用于支持 react 操作 dom
		- babel.min.js
			- 用于将 [[JSX]] 转为 js
		- #+BEGIN_NOTE
		  引入的顺序不能错
		  #+END_NOTE
	- 渲染 `Hello, World!`
		- 在 vsc 中添加如下代码
			- ``` html
			  <!DOCTYPE html>
			  <html lang="en">
			  <head>
			      <meta charset="UTF-8">
			      <title>hello_react</title>
			  </head>
			  <body>
			      <div id="test"></div>
			      <script type="text/javascript" src="../dep_old/react.development.js"></script>
			      <script type="text/javascript" src="../dep_old/react-dom.development.js"></script>
			      <script type="text/javascript" src="../dep_old/babel.min.js"></script>
			  
			      <script type="text/babel">
			          const vdom = <h1>Hello, world!</h1>;
			          ReactDOM.render(vdom, document.getElementById('test'));
			      </script>
			  </body>
			  </html>
			  ```
		-