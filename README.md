# Jsrsey、RESTEasy、Spark Framework和SpringMVC 框架比较

参照[最好的8个 Java RESTful 框架][1]和[Java RESTful框架的性能比较][2] 选择4个适于契约锁web开发的框架
## 一、框架比较
从网上找的一些资料，内容不完善而且可能有错误的地方
### **1.Jsrsey**
Jersey RESTful 框架是开源的RESTful框架, 实现了JAX-RS (JSR 311 & JSR 339) 规范。它扩展了JAX-RS 参考实现， 提供了更多的特性和工具， 可以进一步地简化 RESTful service 和 client 开发。尽管相对年轻，它已经是一个产品级的 RESTful service 和 client 框架。

**链接**
[官方站点][3] [GITHUB][4] [文档][5]

**优点**

- 优秀的文档和例子
- 快速
- 超级容易的路由
- 平滑的 JUnit 集成
- 就个人而言, 当开发 RESTful service 时, JAX-RS 实现要好于 MVC 框架。
- 可以集成到其它库/框架 (Grizzly, Netty). 这也可能是很多产品使用它的原因。
- 支持异步链接
- 不喜欢 servlet container? 使用Jersey的时候可以不用它们。
- WADL, XML/JSON support
- 包含在Glassfish中

**缺点**

- Jersey 2.0+使用了有些复杂的依赖注入实现
- 可能不是一件坏事。Jersey 1.X 使用较老的 JAX-RS 实现
- 一大堆第三方库只支持 Jersey 1.X， 在 Jersey 2.X 不可用

**例子**
```java
@Path("/test")
@Component
public class TestController {
	@GET
	@Consumes({ MediaType.TEXT_PLAIN })
	@Produces({ MediaType.APPLICATION_JSON })
	public Message  getTest() throws InterruptedException{
		System.out.println("调用 test...");
		Thread.sleep(100);   
		return new Message("hello world!!");
	}
}
```

### **2.RESTEasy**
RESTEasy是JBoss的一个开源项目，提供各种框架帮助你构建RESTful Web Services和RESTful Java应用程序。它是JAX-RS规范的一个完整实现并通过JCP认证。作为一个JBOSS的项目，它当然能和JBOSS应用服务器很好地集成在一起。但是，它也能在任何运行JDK5或以上版本的Servlet容器中运行。RESTEasy还提供一个RESTEasy JAX-RS客户端调用框架。能够很方便与EJB、Seam、Guice、Spring和Spring MVC集成使用。支持在客户端与服务器端自动实现GZIP解压缩。

**链接**
[官方站点][6] [GITHUB][7] [文档][8]

**优点**

- 不需要配置文件，只要把JARs文件放到类路径里面，添加 @Path 标注就可以了。
- 完全的把 RESTEeasy 配置作为Seam 组件来看待。
- HTTP 请求由Seam来提供，不需要一个额外的Servlet。
- Resources 和providers可以作为 Seam components (JavaBean or EJB)，具有全面的Seaminjection,lifecycle, interception, 等功能支持。
- 支持在客户端与服务器端自动实现GZIP解压缩。

**缺点**

- 与jersey和spark framework相比有点厚重

**例子**
```java
@Path("/test")
@Component
public class TestController {
	@GET
	@Consumes({ MediaType.TEXT_PLAIN })
	@Produces({ MediaType.APPLICATION_JSON })
	public Message  getTest() throws InterruptedException{
		System.out.println("调用 test...");
		Thread.sleep(100);   
		return new Message("hello world!!");
	}
}
```

### **3.Spark Framework**
不要和 Apache 的大数据框架 Spark 弄混, 这里的 Spark 框架是一个轻量级的 Java web 框架，用来进行快速的开发(50% Spark用户使用 Spark 创建 REST APIs)。 它受 Ruby 框架 Sinatra 启发。
它有一个不到1M的最小化的内核， 提供了所有基本的特性, 用来构建 RESTful 或者传统的 web 应用程序。
**链接**
[官方站点][9] [GITHUB][10] [文档][11]

**优点**

- 快，轻量级
- 优秀的快速原型
- 易于搭建
- 经常和AngularJS搭配使用
- 真正的微框架
- 使用 Jetty
- 可以用在容器中或者独立运行

**缺点**

- 文档可以更好，它不适合初学者
- 不适合大型项目
- 社区小

**例子**
```java
get("/rest/test", (request, response) -> {
   System.out.println("调用 test...");
   Thread.sleep(100);   // 
   return new Message("hello world!!");
});
```

### **4.SpringMVC**
已经是非常成熟的框架了，相关文档到[官网][12]去看

## 二、四种框架性能比较
将四种框架运用到SpringBoot中，在相同环境启动，相应的类加载量、堆栈和线程数比较如下：
### 类加载量
![类加载量比较][13]
### 启动与运行过程中JVM信息
![jvm信息][14]
### 压力测试
四种框架在相同环境下，并发量100执行10000次请求得到的数据如下：
![压力测试][15]



  [1]: http://colobu.com/2015/11/15/best-available-java-restful-micro-frameworks/
  [2]: http://blog.csdn.net/shizhiailian/article/details/52422814
  [3]: https://jersey.github.io/
  [4]: https://github.com/jersey/jersey
  [5]: https://jersey.github.io/
  [6]: http://resteasy.jboss.org/
  [7]: https://github.com/resteasy/Resteasy
  [8]: http://resteasy.jboss.org/docs
  [9]: http://sparkjava.com/
  [10]: https://github.com/perwendel/spark
  [11]: http://sparkjava.com/documentation.html
  [12]: http://spring.io/
  [13]: ./picture/class_loading.png
  [14]: ./picture/start_run.png
  [15]: ./picture/stress_test.png