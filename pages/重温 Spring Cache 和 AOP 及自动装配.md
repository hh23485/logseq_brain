tags:: Java, Spring Framework, Spring Cache, AOP, 架构设计

- 前言
	- 上次读 Spring 是很久以前的事情了，最近工作需要在改造一个工作流引擎，想要针对其中的每个工作节点加入缓存，但遇到很多在 Java 界早就被 Spring 解决的很好，但 C# 界或者说我部门还无人问津的事情，例如：
		- 如何侵入的向系统内加入缓存？
		- 如何无侵入的做到多级缓存？
		- 如何做到 AOP 编程？
		- 如何做到像插件一样自动装配？
	- 这些问题的答案是互相包含的，总之，我们在寻求一种类似 Spring Cache 的体验，当在系统中开启配置之后，无需做任何代码的修改，就能自动为所有的节点或者特定的节点开启缓存，无侵入，轻量级。
	- 然而，Spring 能做到这些，必然是依赖了 [[Dependency Injection]] 和 [Spring AOP]。但在 .Net 4.7.2 还没有这些官方的功能，在现有的系统中，即便使用 [[AutoFac]] 这样的依赖注入库，想要复现完整的体验，也不是一个容易的事情。所以再次重温一下 Spring Cache 的实现和自动装配的知识，看看如何最小的改动来支撑需求。
- Spring Cache 的使用体验
	- 开启
		- 使用 @Cacheable 来表示在方法调用前先查询缓存，如果有缓存就跳过调用
		- 使用 `@CachePut` 来表示在方法调用后，要写入缓存
		- 使用 `@CacheEvict` 表示调用时会使缓存失效
	- 配置
	- 好处
		- 提供了注解访问，对代码侵入少，耦合低，甚至完全透明
		- 提供了 [Cache 抽象](((63762220-f82f-4eb9-bb2e-c6f6a2ef675f)))，可以轻松的替换底层缓存存储
		- 可以和事务一起回滚
		- 支持比较复杂的缓存逻辑
		- #+BEGIN_QUOTE
		  [Spring Cache 抽象详解](https://www.pudn.com/news/62615bc10e75e42012407a76.html)
		  #+END_QUOTE
- 实现
	- Cache 抽象
	  id:: 63762220-f82f-4eb9-bb2e-c6f6a2ef675f
		- Cache 接口
			- ``` java
			  package org.springframework.cache;  
			    
			  public interface Cache {  
			      String getName();  //缓存的名字  
			      Object getNativeCache(); //得到底层使用的缓存，如Ehcache  
			      ValueWrapper get(Object key); //根据key得到一个ValueWrapper，然后调用其get方法获取值  
			      <T> T get(Object key, Class<T> type);//根据key，和value的类型直接获取value  
			      void put(Object key, Object value);//往缓存放数据  
			      void evict(Object key);//从缓存中移除key对应的缓存  
			      void clear(); //清空缓存  
			    
			      interface ValueWrapper { //缓存值的Wrapper  
			        Object get(); //得到真实的value  
			      }
			  }  
			  ```
	- 默认实现
		- `ConcurrentMapCacheManager`
		- `GuavaCacheManager`
		- `EhCacheCacheManager`
		- `JCacheCacheManager`
	- Cache 的组合
		- 提供了 `CompositeCacheManager` 接口，可以从多个 CacheManager 中查询
		-