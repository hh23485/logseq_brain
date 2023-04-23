tags:: 尚硅谷, React

- {{embed [[React 函数式组件]]}}
- {{embed [[React 类式组件]]}}
- [[React 组件的三大属性]]
- React 的事件处理
	- React 的事件处理是重新实现的，签名为 onXxxx，可以实现更高效和兼容性更好的处理
	- 事件触发时会传递 event 参数，`event.target` 就是触发事件的节点
		- 可以代替部分 ref
- 收集表单数据
	- 非受控组件
		- 使用 `event.preventDefault()` 阻止原生 form 提交事件跳转
	- 受控组件