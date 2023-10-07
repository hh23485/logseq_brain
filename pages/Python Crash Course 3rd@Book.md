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
			-