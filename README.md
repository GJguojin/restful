# Jsrsey��RESTEasy��Spark Framework��SpringMVC ��ܱȽ�

����[��õ�8�� Java RESTful ���][1]��[Java RESTful��ܵ����ܱȽ�][2] ѡ��4��������Լ��web�����Ŀ�ܣ���д����Ӧ�ļ����ӣ�ֻ��hello world������,����ȫ��ʹ����SpringBoot,��������ʹ�õ���jetty��
[SpringBoot_jsersey][3]��[SpringBoot_RESTEasy][4]��[SpringBoot_sparkFramework][5]��[SpringBoot_springVC][6]

---

## һ����ܱȽ�
�������ҵ�һЩ���ϣ����ݲ����ƶ��ҿ����д���ĵط�
### **1.Jsrsey**
Jersey RESTful ����ǿ�Դ��RESTful���, ʵ����JAX-RS (JSR 311 & JSR 339) �淶������չ��JAX-RS �ο�ʵ�֣� �ṩ�˸�������Ժ͹��ߣ� ���Խ�һ���ؼ� RESTful service �� client ����������������ᣬ���Ѿ���һ����Ʒ���� RESTful service �� client ��ܡ�

**����**
[�ٷ�վ��][7] [GITHUB][8] [�ĵ�][9]

**�ŵ�**

- ������ĵ�������
- ����
- �������׵�·��
- ƽ���� JUnit ����
- �͸��˶���, ������ RESTful service ʱ, JAX-RS ʵ��Ҫ���� MVC ��ܡ�
- ���Լ��ɵ�������/��� (Grizzly, Netty). ��Ҳ�����Ǻܶ��Ʒʹ������ԭ��
- ֧���첽����
- ��ϲ�� servlet container? ʹ��Jersey��ʱ����Բ������ǡ�
- WADL, XML/JSON support
- ������Glassfish��

**ȱ��**

- Jersey 2.0+ʹ������Щ���ӵ�����ע��ʵ��
- ���ܲ���һ�����¡�Jersey 1.X ʹ�ý��ϵ� JAX-RS ʵ��
- һ��ѵ�������ֻ֧�� Jersey 1.X�� �� Jersey 2.X ������

**����**
```java
@Path("/test")
@Component
public class TestController {
	@GET
	@Consumes({ MediaType.TEXT_PLAIN })
	@Produces({ MediaType.APPLICATION_JSON })
	public Message  getTest() throws InterruptedException{
		System.out.println("���� test...");
		Thread.sleep(100);   
		return new Message("hello world!!");
	}
}
```

### **2.RESTEasy**
RESTEasy��JBoss��һ����Դ��Ŀ���ṩ���ֿ�ܰ����㹹��RESTful Web Services��RESTful JavaӦ�ó�������JAX-RS�淶��һ������ʵ�ֲ�ͨ��JCP��֤����Ϊһ��JBOSS����Ŀ������Ȼ�ܺ�JBOSSӦ�÷������ܺõؼ�����һ�𡣵��ǣ���Ҳ�����κ�����JDK5�����ϰ汾��Servlet���������С�RESTEasy���ṩһ��RESTEasy JAX-RS�ͻ��˵��ÿ�ܡ��ܹ��ܷ�����EJB��Seam��Guice��Spring��Spring MVC����ʹ�á�֧���ڿͻ�������������Զ�ʵ��GZIP��ѹ����

**����**
[�ٷ�վ��][10] [GITHUB][11] [�ĵ�][12]

**�ŵ�**

- ����Ҫ�����ļ���ֻҪ��JARs�ļ��ŵ���·�����棬��� @Path ��ע�Ϳ����ˡ�
- ��ȫ�İ� RESTEeasy ������ΪSeam �����������
- HTTP ������Seam���ṩ������Ҫһ�������Servlet��
- Resources ��providers������Ϊ Seam components (JavaBean or EJB)������ȫ���Seaminjection,lifecycle, interception, �ȹ���֧�֡�
- ֧���ڿͻ�������������Զ�ʵ��GZIP��ѹ����

**ȱ��**

- ��jersey��spark framework����е����

**����**
```java
@Path("/test")
@Component
public class TestController {
	@GET
	@Consumes({ MediaType.TEXT_PLAIN })
	@Produces({ MediaType.APPLICATION_JSON })
	public Message  getTest() throws InterruptedException{
		System.out.println("���� test...");
		Thread.sleep(100);   
		return new Message("hello world!!");
	}
}
```

### **3.Spark Framework**
��Ҫ�� Apache �Ĵ����ݿ�� Spark Ū��, ����� Spark �����һ���������� Java web ��ܣ��������п��ٵĿ���(50% Spark�û�ʹ�� Spark ���� REST APIs)�� ���� Ruby ��� Sinatra ������
����һ������1M����С�����ںˣ� �ṩ�����л���������, �������� RESTful ���ߴ�ͳ�� web Ӧ�ó���
**����**
[�ٷ�վ��][13] [GITHUB][14] [�ĵ�][15]

**�ŵ�**

- �죬������
- ����Ŀ���ԭ��
- ���ڴ
- ������AngularJS����ʹ��
- ������΢���
- ʹ�� Jetty
- �������������л��߶�������

**ȱ��**

- �ĵ����Ը��ã������ʺϳ�ѧ��
- ���ʺϴ�����Ŀ
- ����С

**����**
```java
get("/rest/test", (request, response) -> {
   System.out.println("���� test...");
   Thread.sleep(100);   // 
   return new Message("hello world!!");
});
```

### **4.SpringMVC**
�Ѿ��Ƿǳ�����Ŀ���ˣ�����ĵ���[����][16]ȥ��

---

## �������ֿ�����ܱȽ�
�����ֿ�����õ�SpringBoot�У�����ͬ������������Ӧ�������������ջ���߳����Ƚ����£�[��������][17]����
### �������
![��������Ƚ�][18]
### ���������й�����JVM��Ϣ
![jvm��Ϣ][19]
### ѹ������
���ֿ������ͬ�����£�������100ִ��10000���������������з�����ģ��ҵ����ʱ��Ϊ100ms�����õ����������£�
![ѹ������][20]

## �����ܽ�
�����������п��ǿ�����

- SpringMVC�������ۡ� 
- Spark Framework�������ţ��������Ϸ�װ���ڼ�ª��ʹ���俪����������Ŀ�޸Ĺ��󣬶��ҿ��̫���������Ĳ��ֹ��ܲ���ʵ�֡�
- RESTEasy�������ţ�������SpringBootʹ����������SpringMVC.jar,ʹ�������е���ء�
- Jsrsey���ܴ�������֮�䣬�����Ƽ�ʹ�á�


  [1]: http://colobu.com/2015/11/15/best-available-java-restful-micro-frameworks/
  [2]: http://blog.csdn.net/shizhiailian/article/details/52422814
  [3]: https://github.com/GJguojin/SpringBoot_jsersey.git
  [4]: https://github.com/GJguojin/SpringBoot_RESTEasy.git
  [5]: https://github.com/GJguojin/SpringBoot_sparkFramework.git
  [6]: https://github.com/GJguojin/SpringBoot_springMVC.git
  [7]: https://jersey.github.io/
  [8]: https://github.com/jersey/jersey
  [9]: https://jersey.github.io/
  [10]: http://resteasy.jboss.org/
  [11]: https://github.com/resteasy/Resteasy
  [12]: http://resteasy.jboss.org/docs
  [13]: http://sparkjava.com/
  [14]: https://github.com/perwendel/spark
  [15]: http://sparkjava.com/documentation.html
  [16]: http://spring.io/
  [17]: https://github.com/GJguojin/restful.git
  [18]: ./picture/class_loading.png
  [19]: ./picture/start_run.png
  [20]: ./picture/stress_test.png