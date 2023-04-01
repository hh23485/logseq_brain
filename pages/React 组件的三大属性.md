- State
	- state 是组件的重要属性之一，用于保存组件的状态
	- state 默认是 `null`，要求 state 必须是一个对象以存储多种状态，可以设置 `this.state={}`
	- 如何初始化
		-
	- 如何更新
		- 构造函数之外更新 state 不能直接赋值，需要通过 `setState`
			- ``` js
			  this.setState({ age: 18 })
			  ```
	- 可以通过 `const {age, name} = this.state` 从其中获取多个属性
	-