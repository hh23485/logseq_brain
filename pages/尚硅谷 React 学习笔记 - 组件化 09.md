tags:: 尚硅谷, React

- 函数式组件
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
		- 标签需要首字母大写