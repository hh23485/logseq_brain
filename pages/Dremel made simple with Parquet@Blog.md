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
					- 该层可空，往上不可空，所以在可空的第一层
				- `contacts.name`: 1
					- `contacts.name` 是 `required` 元素，因此 `contacts` 如果有子元素，就一定存在，contacts 可能 `null`，因此层级是 1
				- `contacts.phoneNumber`: 2
					- `phoneNumber` 是 `optional` 元素，层级比 `name` 要低一级，是 2
					- 另外一个角度的理解是，即便 contacts 的某个对象存在，只能保证 name 存在，不能保证 `phoneNumber` 存在，所以他们并不在同一个定义层级上
- ## Repetition level
	- 重复级别表示：必须为当前值创建新列表的级别
		- 这句话很难懂，但以如下例子来解释
			- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet105.thumb.1280.1280.png)
			  id:: 64f082b3-11ad-4ae6-b965-bf952718f664
			- 在这个例子中，如果显示嵌套级别，可以得到
				- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet107.thumb.1280.1280.png)
				- 如果解释这个图
					- 对于 a，定义了第 0 层的元素
					  logseq.order-list-type:: number
					- 对于 b，定义了第 1 层的新元素
					  logseq.order-list-type:: number
					- 对于 c，定义了第 2 层的新元素
					  logseq.order-list-type:: number
					- 对于 d，定义了第 1 层的新元素
					  logseq.order-list-type:: number
					- 对于 e，定义了第 2 层的新元素
					  logseq.order-list-type:: number