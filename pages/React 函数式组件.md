- 将标签放在一个函数中，并将该函数以标签的形式渲染到 Dom
- 样例
	- ``` js
	  function Demo() {
	  return <h2>hello 函数式组件</h2>;
	  }
	  
	  ReactDOM.render(<Demo />, document.getElementById("test"));
	  
	  ```
- 注意
	- 将函数名作为标签
	- 标签需要首字母大写，否则会报错
	  background-color:: red
		- {{embed ((6427dbd5-fb0a-4de1-bfad-7316d8dea0fd))}}
- 发生了什么事情
	- React 解析组件标签，尝试找 Demo 组件
	- 发现组件是函数定义的，调用函数
	- 将函数的返回值进行渲染