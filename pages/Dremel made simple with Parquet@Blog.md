tags:: Parquet

- [Dremel made simple with Parquet (twitter.com)](https://blog.twitter.com/engineering/en_us/a/2013/dremel-made-simple-with-parquet)
- 事实上这篇文章在用一种更容易的方式解释 Parquet Columnar format
- 单一的列并不困难，但如何处理嵌套元素？
	- 其中的核心是 Definition level 和 Repetition level
- 我读了好几遍才能勉强理解，那么将我理解后的内容记录如下：
- ## Definition level
	- 用来定义这个字段所属的字段树的层级，可以快速的通过层级来判定这些