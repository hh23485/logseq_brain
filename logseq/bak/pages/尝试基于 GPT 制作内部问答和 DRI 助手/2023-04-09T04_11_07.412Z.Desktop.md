tags:: GPT Plugin, 复刻, Azure Bot, Lang-Chain

- 前置调研
  collapsed:: true
	- 抛开模型本身，复刻 ChatGPT 类似的系统并不是一件困难的事情，通常需要
		- GPT 接口
		- 可对话的 UI
		- 可管理会话上下文的组件
		- 流式输出的 Client
	- 在此基础上，为了增强对现有知识库的理解，可产生需求：
		- 如何和 PDF 对话
		- 如何和资料库对话
		- 如何和多个书对话
	- 这些任务本身是复杂的，但基于开源社区和 GPT，清晰的流程和开源工具短短时间已经相对成熟
		- PDF 分割：任何 PDF 工具均可
		- Embedding：开源工具，OpenAI 接口，集成了开源模型的向量数据库，如 Chroma, Milvus 等，Azure Semantic Search 服务
		- Lang-Chain：提供胶水代码，集成上述所有工具的工作流，并建立了较多的生态和prompt模板。除此之外，还包括了类似 Plugin 的基于 Action 的模版应答机制可以将预定义的工具引入工作流。
- 资源
  collapsed:: true
	- GPT 接口
	- Lang-Chain 框架
	- Python 3.10
	- Chroma
	- Lang-Chain UI
	- AAD
- 要解决的问题
	-
- 参考资料
	- 关于如何解决 api 接口认证问题
		- [(97) Discord | "Google Colaboratory" | LangChain](https://discord.com/channels/1038097195422978059/1047066966566916107/1048742148268359710)