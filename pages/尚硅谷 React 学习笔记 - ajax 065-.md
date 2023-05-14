tags:: React, axios

- 测试跨域代理配置
	- 简单配置
		- 在 `package.json` 中添加配置
		- ``` json
		  "proxy": "http://localhost:5000"
		  ```
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
				- `pathRewrite`: 用于去除 path 中本地用于分发的代码，还原成实际想要
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