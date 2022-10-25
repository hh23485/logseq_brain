tags:: AnyType, CRDT

- # 背景
	- [[AnyType]] 在我参加的第一个内测版本中就已经做到了自动冲突解决，比起 Logseq 不得不使用 Git 或者 Onedrive 笨拙的同步文件，经常被搞得非常凌乱，更不要提还想要进行多人协同。
	- 今天看到 [[Obsidian]] 有人发布了 [remotely-save/remotely-save (github.com)](https://github.com/remotely-save/remotely-save)，提供了单人的基于文件的同步，但显然也强调了 `No Conflict resolution. No content-diff-and-patch algorithm`，那么对于 Logseq 的长期使用，就希望也存在一种插件能够做到类似 AnyType 的效果
	- 重新去翻了一下 AnyType 当初的讨论 [Conflict handling when syncing - Feature Requests - Anytype Community](https://community.anytype.io/t/conflict-handling-when-syncing/1373)，加上当时体验的感受，觉得 [[CRDT]] 也许是一个不错的入手点，如果机制不那么复杂的话完全可以自己写一个。
- # 资料
	- AnyType 提及了完整介绍 CRDT 的文章 [Local-first software: You own your data, in spite of the cloud (inkandswitch.com)](https://www.inkandswitch.com/local-first/)
- # 主题
	- ## 什么是 CRDT
	- ## 为什么需要 CRDT
	- ## CRDT 是如何工作的