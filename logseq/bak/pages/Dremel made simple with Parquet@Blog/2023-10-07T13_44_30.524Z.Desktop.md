tags:: Parquet

- /toc
- TOC {{renderer :tocgen, [[]], 2, h}}
- 博客
	- [Dremel made simple with Parquet (twitter.com)](https://blog.twitter.com/engineering/en_us/a/2013/dremel-made-simple-with-parquet)
	- 事实上这篇文章在用一种更容易的方式解释 Parquet Columnar format
	- 单一的列并不困难，但如何处理嵌套元素？
		- 其中的核心是 Definition level 和 Repetition level
- 我读了好几遍才能勉强理解，那么将我理解后的内容记录如下：
	- ## 从这个案例开始
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
			- 需要注意的是：
				- AddressBook 是根元素
				- `required` 表示这个元素只要上层存在，那么它肯定存在
				- `repeated` 表示是一个列表
				- 分支表示是上一层的成员
		- 将图展开成盒型图如下所示
			- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet101.thumb.1280.1280.png)
	- ## Definition level
		- To support nested records we need to store the level for which the field is null. This is what the definition level is for: from 0 at the root of the schema up to the maximum level for this column。也就是定义从 root 到当前层，在可 `null`  的第几层
			- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet103.thumb.1280.1280.png){:height 399, :width 923}
			- 可以快速的通过层级来判定这个嵌套层级到哪一层是有数据的
		- 用图来表达之前 `AddressBook` 的例子
			- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet100.thumb.1280.1280.png){:height 423, :width 890}
		- 根据定义得到 Definition level：
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
					- 对于这个图，我自己解释为：
						- 对于 a，定义了第 0 层的新元素
						  logseq.order-list-type:: number
						- 对于 b，定义了第 1 层的新元素
						  logseq.order-list-type:: number
						- 对于 c，定义了第 2 层的新元素
						  logseq.order-list-type:: number
						- 对于 d，定义了第 1 层的新元素
						  logseq.order-list-type:: number
						- 对于 e，定义了第 2 层的新元素
						  logseq.order-list-type:: number
						- ...
						  logseq.order-list-type:: number
					- 初看的时候，不能理解什么叫定义层级的新元素。
					- 事实上在存储的时候，并不会给你一个树状结构，而是一个扁平的结构，一个列中只有一个 level 2，那么如果你发现它的重复级别是 0，就表示一个新的 Nested lists 的元素，它和另外一个重复级别是 0 的记录一定不在同一个 Nested lists 中
					- 如果你想要查找一个 Nested lists 所有的元素，你就扫描到下一个 0 就可以了，如果你想要找到同一个 Level1 的，你就找到下一个为 1 的
- 所以综合上面的两个新概念，可以得到上述例子中的各个字段的 D 和 R
	- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet108.thumb.1280.1280.png){:height 315, :width 989}
- 最后
	- 作者给了一个实际的记录模拟
		- 对于数据
			- ``` protobuf
			  AddressBook {
			      contacts: {
			              phoneNumber: "555 987 6543"
			          }
			          contacts: {
			          }
			      }
			  AddressBook {
			  }
			  ```
		- 假如看 `contacts.phoneNumber` 这列
			- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet109.thumb.1280.1280.png)
		- 可以得到如下解释：
			- `0`,` 2`, `"555 987 6543"`
				- `0` 表示定义了一个新的 `AddressBook`
				- `2` 表示定义到了层级 2, 这一层有值
				- 值为 `555 987 6543`
			- `1`, `1`
				- `1` 表示在同一个 `AddressBook` 中定义了一个新的 `contacts`
				- `1` 表示没有定义到层级2，也就是只包含 `name`，`phoneNumber` 这一列没有值
			- `0`, `0`
				- `0` 表示一个新的 `AddressBook`
				- `0` 表示没有定义任何的 `contacts`
		- 最后存储的结果为
			- ![Dremel made simple with Parquet](https://cdn.cms-twdigitalassets.com/content/dam/blog-twitter/archive/dremel_made_simplewithparquet110.thumb.1280.1280.png){:height 273, :width 501}
	- 那么层级关系可以被很容易的存储，3 个 bit 就可以处理 7 层嵌套，而没有嵌套的列不会有 R 和 D
	- 对于这种有 schema 的结构，即便是嵌套的列式存储，也可以进行高效编码压缩