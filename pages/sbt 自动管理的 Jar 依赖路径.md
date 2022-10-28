tags:: ivy, sbt

- Docs
	- [sbt Reference Manual — Library Management (scala-sbt.org)](https://www.scala-sbt.org/1.x/docs/Library-Management.html)
- sbt 可以 [手动管理依赖](https://www.scala-sbt.org/1.x/docs/Library-Management.html#Manual+Dependency+Management)
	- 通过声明将 `unmanagedBase` 路径配置好，然后指定 `unmanagedJars`
		- ``` sbt
		  https://www.scala-sbt.org/1.x/docs/Library-Management.html#Manual+Dependency+Management
		  Compile / unmanagedJars := (baseDirectory.value ** "*.jar").classpath
		  ```
- 在 [自动管理](https://www.scala-sbt.org/1.x/docs/Library-Management.html#Automatic+Dependency+Management) 的情况下，sbt 自 1.3 开始使用 [[Coursier]] 和 [[Apache lvy]] 一起实现
	- 开关
		- ``` sbt
		  ThisBuild / useCoursier := false
		  ```
	- 声明
		- ``` sbt
		  libraryDependencies += groupID % artifactID % revision
		  # or
		  libraryDependencies += groupID % artifactID % revision % configuration
		  ```
	- jar 存储位置
		- `~/.ivy2/jars`
		- ![image.png](../assets/image_1666953965970_0.png){:height 409, :width 1386}