tags:: [[React 组件]]

- JS 中类和 Java 基础语法很像
	- extends 继承
	- super 关键字
	- this 指向当前对象
	- constructor 声明构造方法
	- member function 可以传入对象当做 this 使用
- 创建 react 组件，继承 `React.Component`
	- 如果需要传入参数，可以在 props 后加入新的构造参数
	- 额外参数可以在渲染标签时作为属性加入
- 样例
	- ``` js
	  class Student extends React.Component {
	    constructor(props, name, age) {
	      super(props);
	      this.state = {
	        name: "hello",
	        age: 18,
	      };
	    }
	  
	    render() {
	      return (
	        <div>
	        <h1>{this.state.age}</h1>
	        <h2>hello</h2>
	        </div>
	      );
	    }
	  }
	  ReactDOM.render(<Student />, document.getElementById("test"));
	  ```