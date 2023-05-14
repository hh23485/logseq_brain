- SPA
  collapsed:: true
	- 单页 Web 应用
	- 整个应用只有一个完整的页面
	- 点击站内链接不会刷新页面，只做页面局部更新
	- 数据全都通过 ajax 请求获取，在前端异步展示
- 实现
	- 依赖路由
- 前端路由
	- 什么是路由
	  collapsed:: true
		- 一个路由就是一个映射关系
			- key 是路径
			- value 是 component
	- 原理
	  collapsed:: true
		- 浏览器 History 管理
			- 假设使用 history.js
				- 使用 `listen` 监听 location 变化，获取路径变化事件
				- 使用 `push` 来前进
				- 使用 `replace` 来替换栈顶
				- 使用 `back` 来回退
				- `History.createBrowserHistory()`
					- 使用 HTML5 的 API
				- `History.createHashHistory()`
					- 路径中加入 `#`
					- 引起锚点跳转，即路径发生变化，但不引发刷新
					- 兼容性更好
		- 在检测到路径变化后，就可以替换对应的组件关系
- 组件库
	- react-router-dom
		- 专为 web 设计的 react 路由插件库
		- 使用
			- 在最外层包裹 `BrowserRouter` 标签
			- 使用 `Link` 代替 `a` 标签
				- ``` jsx
				  <Link className="list-group-item" to="/home">
				    Home
				  </Link>
				  ```
			- 使用 `Route` 嵌入组件内容
				- ``` jsx
				  <Route path="/home" component={Home} />
				  ```
- 路由组件与一般组件
	- 路由组件映射的组件会收到路由器传入的 props
		- history
			- go: func
			- goBack: func
			- goForward: func
			- push: func
			- replace: func
		- location
			- pathname
			- search
			- state
		- match
			- isExact
			- path
			-
	- 路由组件由 `Route` 标签控制，一般组件要手动写入
	- 存放位置不同，路由组件通常放在 pages 底下，一般组件放在 componenets 下
-