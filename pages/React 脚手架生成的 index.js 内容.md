tags:: [[create-react-app]]

- 生成的内容
	- ``` javascript
	  import React from 'react';
	  import ReactDOM from 'react-dom/client';
	  
	  // 放入通用的 css 样式
	  import './index.css';
	  
	  // 引入 App 组件
	  import App from './App';
	  import reportWebVitals from './reportWebVitals';
	  
	  // 渲染 react root dom
	  const root = ReactDOM.createRoot(document.getElementById('root'));
	  root.render(
	    <React.StrictMode>
	      // 添加组件
	      <App />
	    </React.StrictMode>
	  );
	  
	  // 上报性能
	  // If you want to start measuring performance in your app, pass a function
	  // to log results (for example: reportWebVitals(console.log))
	  // or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
	  reportWebVitals();
	  
	  
	  ```