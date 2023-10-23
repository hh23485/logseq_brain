tags:: Checklist, [[Machine Learning]], [[Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow, 3rd Edition@Books]]

- 这个清单可以指导您完成机器学习项目。有八个主要步骤：
	- 框定问题并审视整体情况。
	  logseq.order-list-type:: number
	- 获取数据。
	  logseq.order-list-type:: number
	- 探索数据以获得洞察。
	  logseq.order-list-type:: number
	- 准备数据以更好地暴露底层数据模式给机器学习算法。
	  logseq.order-list-type:: number
	- Explore many different models and shortlist the best ones.
	  logseq.order-list-type:: number
	- 优化您的模型并将它们组合成一个出色的解决方案。
	  logseq.order-list-type:: number
	- Present your solution.
	  logseq.order-list-type:: number
	- 启动、监控和维护您的系统。
	  logseq.order-list-type:: number
- 显然，您可以根据自己的需求自由调整此清单。
- ## 确定问题并全局观察
	- 以商业术语定义目标
	  logseq.order-list-type:: number
	- 您的解决方案将如何使用？
	  logseq.order-list-type:: number
	- 如果有的话，目前有哪些解决方案/变通方法？
	  logseq.order-list-type:: number
	- 你应该如何构建这个问题（有监督/无监督，在线/离线等）？
	  logseq.order-list-type:: number
	- 性能应该如何衡量？
	  logseq.order-list-type:: number
	- 绩效指标是否与业务目标一致？
	  logseq.order-list-type:: number
	- 达到业务目标所需的最低性能是多少？
	  logseq.order-list-type:: number
	- 什么是可比较的问题？你能重复使用经验或工具吗？
	  logseq.order-list-type:: number
	- 人类专业知识是否可用？
	  logseq.order-list-type:: number
	- How would you solve the problem manually?
	  logseq.order-list-type:: number
	- 列出您（或他人）迄今为止所做的假设。
	  logseq.order-list-type:: number
	- 如有可能，请验证假设。
	  logseq.order-list-type:: number
- ## 获取数据
- 注意：尽量自动化，以便轻松获取最新数据。
	- 列出您所需的数据以及所需的数量。
	  logseq.order-list-type:: number
	- 查找并记录可以获取该数据的位置。
	  logseq.order-list-type:: number
	- 检查需要多少空间。
	  logseq.order-list-type:: number
	- 检查法律义务，并在必要时获得授权。
	  logseq.order-list-type:: number
	- 获取访问授权。
	  logseq.order-list-type:: number
	- 创建一个工作空间（具有足够的存储空间）。
	  logseq.order-list-type:: number
	- 获取数据。
	  logseq.order-list-type:: number
	- 将数据转换为您可以轻松操作的格式（不改变数据本身）。
	  logseq.order-list-type:: number
	- 确保敏感信息被删除或保护（例如，匿名化）。
	  logseq.order-list-type:: number
	- 检查数据的大小和类型（时间序列，样本，地理等）。
	  logseq.order-list-type:: number
	- 抽取一个测试集，将其放在一边，不要查看它（不要进行数据窥探！）。
	  logseq.order-list-type:: number
- ## 探索数据
- Note: try to get insights from a field expert for these steps.
	- 创建数据的副本以进行探索（如果需要，将其缩小到可管理的大小）。
	  logseq.order-list-type:: number
	- 创建一个Jupyter笔记本来记录您的数据探索。
	  logseq.order-list-type:: number
	- 研究每个属性及其特征：
	  logseq.order-list-type:: number
		- 名称
		- 类型（分类的，整数/浮点数，有界/无界，文本，结构化等）
		- 缺失值的百分比
		- 噪声的嘈杂程度和类型（随机噪声、异常值、舍入误差等）
		- 任务的实用性
		- 分布类型（高斯、均匀、对数等）
	- 对于监督学习任务，请确定目标属性。
	  logseq.order-list-type:: number
	- 可视化数据。
	  logseq.order-list-type:: number
	- 研究属性之间的相关性。
	  logseq.order-list-type:: number
	- Study how you would solve the problem manually.
	  logseq.order-list-type:: number
	- 确定您可能想要应用的有前景的转换。
	  logseq.order-list-type:: number
	- 识别额外的数据，这些数据可能会有用（返回“获取数据”）。
	  logseq.order-list-type:: number
	- Document what you have learned.
	  logseq.order-list-type:: number
- ## 准备数据
- 注意事项：
	- 在数据的副本上工作（保持原始数据集完好无损）。
	- 为您应用的所有数据转换编写函数，有五个原因：
	- 所以，下次您获得新的数据集时，您可以轻松地准备数据
		- 所以您可以在未来的项目中应用这些转换
		- 清洁和准备测试集
		- 一旦您的解决方案上线，清理和准备新的数据实例
		- 为了将您的准备选择视为超参数而轻松处理
	- 清理数据
	  logseq.order-list-type:: number
		- 修复或删除异常值（可选）。
		- 填充缺失值（例如，用零、均值、中位数...）或删除它们的行（或列）。
	- 执行特征选择（可选）：
	  logseq.order-list-type:: number
		- 删除对任`务没有有`用信息的属性。 [[#green]]====
	- 进行特征工程，如果适用的话：
	  logseq.order-list-type:: number
		- 离散化连续特征。
		- 分解特征（例如，分类、日期/时间等）。
		- 添加有前景的特征转换（例如，log(x)，sqrt(x)，x 2 ，等等）。
		- 将特征聚合成有前景的新特征。
	- 执行特征缩放
	  logseq.order-list-type:: number
		- 标准化或规范化特征。
- ## 筛选有潜力的模型
- 注意事项：
	- 如果数据量很大，您可能希望对较小的训练集进行抽样，以便在合理的时间内训练多个不同的模型（请注意，这会对复杂模型如大型神经网络或随机森林造成惩罚）。
	- Once again, try to automate these steps as much as possible.
	- 使用标准参数从不同类别（例如线性、朴素贝叶斯、支持向量机、随机森林、神经网络等）训练许多快速而粗糙的模型。
	  logseq.order-list-type:: number
	- 测量和比较它们的性能：
	  logseq.order-list-type:: number
		- 对于每个模型，使用N折交叉验证，并计算在N折上性能度量的均值和标准差。
	- 分析每个算法的最重要变量。
	  logseq.order-list-type:: number
	- 分析模型所产生的错误类型：
	  logseq.order-list-type:: number
		- 人类会使用哪些数据来避免这些错误？
	- 执行快速的特征选择和工程化。
	  logseq.order-list-type:: number
	- 执行五个先前步骤的一到两次快速迭代。
	  logseq.order-list-type:: number
	- 列出前三到五个最有前途的模型，优先选择能够产生不同类型错误的模型。
	  logseq.order-list-type:: number
- ## 优化系统
- 注意事项：
	- 在这一步骤中，您将希望尽可能使用更多的数据，特别是在您朝着微调的最后阶段进行时。
	- 一如既往，自动化你所能自动化的。
	- 使用交叉验证来微调超参数：
	  logseq.order-list-type:: number
		- 将数据转换选择视为超参数，特别是当您对它们不确定时（例如，如果您不确定是用零还是中位数替换缺失值，或者只是删除行）。
		- 除非要探索的超参数值非常少，否则请优先选择随机搜索而不是网格搜索。如果训练时间非常长，您可能更喜欢贝叶斯优化方法（例如，使用高斯过程先验，如Jasper Snoek等人所述）。
	- 尝试集成方法。将您最好的模型组合起来，通常会比单独运行它们产生更好的性能。
	  logseq.order-list-type:: number
	- 一旦您对最终模型有信心，请在测试集上测量其性能以估计泛化误差。
	  logseq.order-list-type:: number
- #+BEGIN_WARNING
  警告
  在测量泛化误差之后不要调整模型：这样只会导致对测试集过拟合。
  #+END_WARNING
- ## Present Your Solution
	- Document what you have done.
	  logseq.order-list-type:: number
	- 创建一个漂亮的演示文稿：
	  logseq.order-list-type:: number
		- 确保首先突出重点。
	- 解释为什么您的解决方案能够实现业务目标。
	  logseq.order-list-type:: number
	- 不要忘记提出你在途中注意到的有趣观点：
	  logseq.order-list-type:: number
		- 描述哪些工作了，哪些没有工作。
	- 列出您的假设和系统的限制。
	  logseq.order-list-type:: number
		- 确保通过美观的可视化或易于记忆的陈述来传达您的关键发现（例如，“中位数收入是房价的头号预测因素”）。
- ## 启动！
	- 准备好您的解决方案以供生产使用（连接到生产数据输入，编写单元测试等）。
	  logseq.order-list-type:: number
	- 编写监控代码，定期检查系统的实时性能，并在性能下降时触发警报
	  logseq.order-list-type:: number
		- 小心慢速退化：随着数据的演变，模型往往会“腐烂”。
		- 测量性能可能需要一个人工流水线（例如，通过众包服务）。
		- 同时监控您的输入质量（例如，故障传感器发送随机值，或其他团队的输出变得陈旧）。这对于在线学习系统尤为重要。
	- 定期使用新鲜数据对模型进行重新训练（尽可能自动化）。
	  logseq.order-list-type:: number
- #+BEGIN_QUOTE
  Jasper Snoek等人，“机器学习算法的实用贝叶斯优化”，第25届神经信息处理系统国际会议论文集2（2012年）：2951-2959。
  #+END_QUOTE
-