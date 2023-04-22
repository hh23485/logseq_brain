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
			  <ComponentClass>.propsTypes = {
			      name: PropTypes.string
			  }
			  ```
				- 函数式组件使用函数名来
		- 要求必传
			- ``` js
			  <ComponentClass>.propsTypes = {
			      name: PropTypes.string.isRequired
			  }
			  ```
		- 默认值
			- ``` js
			  <ComponentClass>.defaultProps = {
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
	-