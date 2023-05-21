tags:: React

- Redux 原理
	- ![image.png](../assets/image_1684582985777_0.png)
	-
- API
	- Dispatch(action)
		- 任何组件可以使用 Dispatch Action 来传递消息给 Store
	- Store
		- Store 存储了之前的状态，或者初始化
		- Reducer 负责处理事件，会收到 Store 发送的 (previousState, action) 的消息，然后 reducer 会处理并返回修改完的状态
		- Store 会重新存储新的 store