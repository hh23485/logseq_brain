tags:: React, axios, PubSub

- 测试跨域代理配置
  collapsed:: true
	- 简单配置
		- 在 `package.json` 中添加配置
		- ``` json
		  "proxy": "http://localhost:5000"
		  ```
		- 优先匹配页面 host 的资源，如果不存在则匹配 target host 的资源
	- 复杂配置
		- 创建 `src/setupProxy.js`
		- 在其中添加如下代码
			- ``` js
			  const proxy = require('http-proxy-middleware')
			  
			  module.exports = function(app) {
			    app.use(
			    	proxy ('/api1', {
			        target: 'http://localhost:5000',
			        changeOrigin: true,
			        pathRewrite: {'^/api1': ''}
			    	})
			    )
			  }
			  ```
				- `changeOrigin`: 控制服务器收到的请求头中的 Host 字段的值
					- `false`: 表示使用页面 host
					- `true`: 表示使用 target host
				- `pathRewrite`: 用于去除 path 中本地用于分发的代码，还原成实际想要请求的路径
			- 但实践中发现该 api 已经废弃需要更换为如下写法
				- ``` js
				  const { createProxyMiddleware } = require('http-proxy-middleware')
				  
				  module.exports = function (app) {
				    app.use(
				      createProxyMiddleware('/api1', {
				        target: 'http://localhost:5000',
				        changeOrigin: true,
				        pathRewrite: { '^/api1': '' }
				      })
				    )
				  }
				  ```
- 搜索 Github 用户样例
	- 消息订阅与发布 PubSub-js
		- 安装 `npm install pubsub-js`
			- 使用 `subscribe` 订阅
				- ``` js
				  componentDidMount() {
				    // 消息会包含两个参数，第一个是 topic，第二个是 data
				    PubSub.subscribe("atguigu", (topic, data) => {
				      // do something
				    });
				  }
				  ```
			- 使用 `unsubscribe` 取消订阅
				- ``` js
				  componentWillUnmount() {
				    PubSub.unsubscribe("atguigu");
				  }
				  ```
			- 使用 `publish` 发送消息
				- ``` js
				  PubSub.publish("atguigu", data);
				  ```
		- 通过 PubSub 来避免使用父组件繁复的传递属性
	- 展示 [[axios]] 的错误消息时返回 `error.message`
	- 展示 [[axios]] 的数据时使用 `response.data`
- 使用 `fetch` 替代 XHR (XMLHttpRequest)
	- ``` js
	  try {
	    const response = await fetch('urlxx')
	    const data = await response.json()
	    console.log(data);
	  } catch (error) {
	    console.log('请求出错', error)
	  }
	  ```
	- 方法上要添加 async 描述符
	-