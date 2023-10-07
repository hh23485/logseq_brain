tags:: [[Books]], [[Python]]

- 第三章
	- List
		- 从列表中删除数据
			- 使用 `del`
				- ``` python
				  motocycles = ['honda', 'yamaha', 'suzuki']
				  print(motocycles)
				  
				  del motocycles[0]
				  print(motocycles)
				  ```
			- 使用 `pop` 移除最后一个项目并返回
			- 使用 `pop(pos)` 移除特定位置的项目并返回
			- 使用 `remove(value)` 移除特定值（第一个）
				- ``` python
				  >>> a = [1,1,2,3,4]
				  >>> a.remove(1)
				  >>> a
				  [1, 2, 3, 4]
				  ```
		- 组织列表
			- 使用 `sort` 进行原地排序
				- ``` python
				  >>> a
				  [1, 2, -1, 3, 4]
				  >>> a.sort()
				  >>> a
				  [-1, 1, 2, 3, 4]
				  ```
			- 使用 `sort(reverse=True)` 进行逆序排序
			- 使用 sorted 传入比较方法进行排序
				- ``` python
				  cars = ['bmw', 'audi', 'toyota', 'subaru']
				  
				  print(cars)
				  print(sorted(cars))
				  print(cars)
				  ```
		- 使用 len 获取 list 的长度
		- 使用负数从后往前访问元素
- 第四章
	- 循环
		- Range(x, y) 生成 [x, y) 的 range 对象，可用于转换成列表或者用于循环
			- ``` python
			  for value in range(1, 6):
			      print(value)
			  
			  numbers = list(range(1, 6))
			  ```
	- 聚合函数
		- min, max, sum 可以应用于 list
	- 列表推导
		- ``` python
		  squares = [value ** 2 for value in range(1, 6)]
		  print(squares)
		  ```
	- 切片
		- 使用  [start:end:step] 来生成切片，切片并不是对原数据的
			- ``` python
			  numbers[:3]
			  numbers[1:3]
			  numbers[::2]
			  numbers[-3:]
			  numbers[0, 4, 1]
			  ```
		- 可以使用 `[:]` 复制一个列宁
		-