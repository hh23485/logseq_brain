tags:: Parquet

- [Dremel made simple with Parquet (twitter.com)](https://blog.twitter.com/engineering/en_us/a/2013/dremel-made-simple-with-parquet)
- 事实上这篇文章在用一种更容易的方式解释 Parquet Columnar format
- 单一的列并不困难，但如何处理嵌套元素？
	- 其中的核心是 Definition level 和 Repetition level
- 我读了好几遍才能勉强理解，那么将我理解后的内容记录如下：
- ## Definition level
	- To support nested records we need to store the level for which the field is null. This is what the definition level is for: from 0 at the root of the schema up to the maximum level for this column。也就是定义从 root 到当前层，在可 `null`  的第几层
		- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet103.thumb.1280.1280.png){:height 399, :width 923}
		- 可以快速的通过层级来判定这个嵌套层级到哪一层是有数据的
	- ### Repeat 和 Group
		- 从这个案例开始
			- ``` protobuf
			  message AddressBook {
			      required string owner;
			      repeated string ownerPhoneNumbers;
			      repeated group contacts {
			          required string name;
			          optional string phoneNumber;
			      }
			  }
			  ```
			- 将图展开成盒型图如下所示
				- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet101.thumb.1280.1280.png)
			- 这个结构和 protobuf 的语法约定相同，用来表达如下的数据结构
				- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet100.thumb.1280.1280.png){:height 423, :width 890}
				- 需要注意的是：
					- AddressBook 是根元素
					- `required` 表示这个元素只要上层存在，那么它肯定存在
					- `repeated` 表示是一个列表
					- 分支表示是上一层的成员
			- 所以和树的结构图不完全一样，可以对 `required` 元素进行压缩，得到定义层级：
				- `owner`: 0
					- owner 是 `required` 元素，因此只要 `AddressBook` 存在，`onwer` 就一定存在，没有可空层
				- `ownerPhoneNumbers`: 1
					- 并不一定存在，但如果存在元素就是 1，如果某行的定义层级为 0，就意味着这行的 `ownerPhoneNumbers` 不存在
				- `contacts.name`: 1
					- `contacts.name` 是 `required` 元素，因此 `contacts` 如果有子元素，就一定存在，层级是 1
				- `contacts.phoneNumber`: 2
					- `phoneNumber` 是 `optional` 元素，可能存在可能不存在，层级要低一级，是 2
					- 另外一个角度的理解是，即便 contacts 的某个对象存在，只能保证 name 存在，不能保证 phoneNumber 存在，所以他们并不在同一个定义层级上
		-