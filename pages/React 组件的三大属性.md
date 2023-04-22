- # state
  id:: 6443d85b-6425-4731-8c3a-a9eee6fa96f7
	- state 是组件的重要属性之一，用于保存组件的状态
	- 如何初始化
		- state 默认是 `null`，要求 state 必须是一个对象以存储多种状态，可以在构造函数里设置 `this.state={}`
		- 直接从成员变量更新
	- 如何更新
		- 构造函数之外更新 state 不能直接赋值，需要通过 `setState`
			- ``` js
			  this.setState({ age: 18 })
			  ```
	- 如何读取
		- `this.state.<var>`
		- 可以通过 `const {age, name} = this.state` 从其中获取多个属性
- # props
  id:: 6443d85b-69c6-403c-943a-49c65ac07476
	- 用于接收标签传入的属性
		- ((64292f8d-8dd2-4adc-ab65-255c3dc63a6b))
	- 限制属性规则
		- 限制类型
			- 引入 `prop-types.js`，引入 `PropTypes`
			- ``` js
			  <ComponentName>.propsTypes = {
			      name: PropTypes.string
			  }
			  ```
		- 要求必传
			- ``` js
			  <ComponentName>.propsTypes = {
			      name: PropTypes.string.isRequired
			  }
			  ```
		- 默认值
			- ``` js
			  <ComponentName>.defaultProps = {
			      name: "DefaultValue"
			  }
			  ```
	- 简写方式
		- ``` js
		  static propTypes = {
		      ...
		  }
		    
		  static defaultProps = {
		    ...
		  }
		  ```
- # rerfs
	- 用于标记组件自身
	- 如何定义
		- 字符串类型
			- ``` js
			  <input
			    type="text"
			    placeholder="点击按钮提示数据"
			    ref="input1"
			  />
			  
			  showData1 = () => {
			    alert(this.refs.input1.value);
			  };
			  ```
		- CreateRefs 类型
			- ``` js
			  constructor()
			  {
			    this.input1 = React.CreateRef()
			  }
			  
			  <input
			    type="text"
			    placeholder="点击按钮提示数据"
			    ref={this.input1}
			  />
			  ```
		- 回调函数形式
			- ``` js
			  <input
			    type="text"
			    placeholder="点击按钮提示数据"
			    // 传递了当前节点
			    ref = { cur => this.input1 = cur }
			  />
			  ```