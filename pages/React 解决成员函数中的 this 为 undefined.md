tags:: React

- 在 React 的类组件中，因为绑定函数给事件时是直接调用，而非通过对象调用，会导致函数中的 this 为 undefined，因此并不能直接使用
- 可参考如下解决方案：
	- 使用 function bind，例如
		- ``` js
		  constructor(props) {
		    super(props);
		    this.state = {
		      hot: false,
		    };
		    this.click = this.handleClick.bind(this);
		  }
		  
		  handleClick() {
		    this.setState({ hot: !this.state.hot });
		  }
		  
		  // <h1 onClick={this.click}>
		  ```
		- 本质是上将原型上的函数在实例对象上又放了一份，`handleClick` 放为 `click`
	- 或者使用 `()=>`
		- ``` js
		  constructor(props) {
		    super(props);
		    this.state = {
		      hot: false,
		    };
		  }
		  
		  handleClick = () => {
		    this.setState({ hot: !this.state.hot });
		  };
		  ```