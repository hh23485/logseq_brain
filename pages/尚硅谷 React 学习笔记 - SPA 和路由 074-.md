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
			- 使用 `NavLink` 用于导航栏 `a` 标签
				- 用 `activeClassName` 来指定 `active` 时添加的 `class` 样式名
			- Switch
				- 多匹配的时候，会全都展示
				- 如果需要单一匹配，则使用 Switch 包裹 Route
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
			- url
	- 路由组件由 `Route` 标签控制，一般组件要手动写入
	- 存放位置不同，路由组件通常放在 pages 底下，一般组件放在 componenets 下
- 多级路径样式丢失问题
	- %PUBLIC_URL%，仅用于 react 脚手架
	- 使用绝对路径，以 `/` 开头
	- 使用 `HashRouter`
- 匹配模式
	- 模糊匹配
		- Link->Route 的匹配是模糊匹配
			- 当 path 为 /home/a/b 时，/home 的 route 也会被触发
	- 精确匹配
		- 添加 exact 在Route 标签中
		- 非必要不打开，会影响二级路由
- 默认匹配
	- `<Redirect to="path" />`
	- 一般卸载所有路由的最下方
- 路由传参
	- 传递 params
		- ``` jsx
		  <Link to ={`/home/message/detail/${id}/${title}`}>{title}</ Link>
		  <Route path="/home/message/detail/:id/:title" component={Detail} />
		  ```
		- 接收时在 `props.match.params` 中
	- 传递 search 参数
		- 类似 query 参数
		- ``` jsx
		  <Link to ={`/home/message/detail?id=${id}&title=${title}`}>{title}</Link>
		  ```
		- `Route` 无需在标签中声明
		- 接收时在 `props.location.search` 中 `?key=value&key=value`，需要手动处理
		- 可以使用 `querystring` 来帮忙切割为 `map`
			- ``` jsx
			  import qs from querystring
			  
			  const {id, title} = qs.parse(search.slice(1)) // remove '?'
			  ```
	- 传递 state 参数
		- 在地址栏上观测不到
		- 传递对象
			- ``` jsx
			  <Link to ={{pathname:'/home/message/detail', state: {id: id, title: title}}}>{title}</Link>
			  ```
		- `Route` 无需在标签中声明
		- 接收时在 `props.location.state`
		- 刷新不会丢失状态，BrowserRouter 会持有状态
- 编程式路由