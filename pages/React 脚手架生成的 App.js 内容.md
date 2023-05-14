tags:: [[React脚手架]]

- 生成的内容
	- ``` javascript
	  // 引入的 logo
	  import logo from './logo.svg';
	  
	  // 引入 css
	  import './App.css';
	  
	  function App() {
	    return (
	      // 函数组件，返回如下 jsx
	      <div className="App">
	        // header 标签
	        <header className="App-header">
	          // 放入图片
	          <img src={logo} className="App-logo" alt="logo" />
	          // 放入一个 p 标签
	          <p>
	            Edit <code>src/App.js</code> and save to reload.
	          </p>
	          // 放入一个 a 标签
	          <a
	            className="App-link"
	            href="https://reactjs.org"
	            target="_blank"
	            rel="noopener noreferrer"
	          >
	            Learn React
	          </a>
	        </header>
	      </div>
	    );
	  }
	  
	  // 暴露函数
	  export default App;
	  ```
-