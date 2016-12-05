---
title: Servlet笔记
date: 2016-11-19 20:54:52
tags: [servlet,JavaWeb]
description: servlet笔记
categories: JavaWeb
---
## Servlet简介
1. Servlet是sun公司提供的一门用于开发**动态web资源**的技术。
2. Sun公司在其API中提供了一个servlet接口，用户若想用发一个动态web资源(即开发一个Java程序向浏览器输出数据)，需要完成以下2个步骤：
	- 编写一个Java类，实现servlet接口;
	- 把开发好的Java类部署到web服务器中;
3. 按照一种约定俗成的称呼习惯，通常我们也把**实现了servlet接口的java程序，称之为Servlet**
4. Servlet是一个供其他Java程序（Servlet引擎）调用的Java类，它不能独立运行，它的运行完全由Servlet引擎来控制和调度。
```java
public interface Servlet {
    void init(ServletConfig var1) throws ServletException;
    ServletConfig getServletConfig();
    void service(ServletRequest var1, ServletResponse var2) throws ServletException, IOException;
    String getServletInfo();
    void destroy();
}
```

## Servlet运行过程
- Servlet程序是由WEB服务器调用，web服务器收到客户端的Servlet访问请求后：
	1. Web服务器首先检查是否已经装载并创建了该Servlet的实例对象。如果是，则直接执行第④步，否则，执行第②步。
	2. 装载并创建该Servlet的一个实例对象。
	3. 调用Servlet实例对象的init()方法。
	4. 创建一个用于封装HTTP请求消息的HttpServletRequest对象和一个代表HTTP响应消息的HttpServletResponse对象，然后调用Servlet的service()方法并将请求和响应对象作为参数传递进去。
	5. WEB应用程序被停止或重新启动之前，Servlet引擎将卸载Servlet，并在卸载之前调用Servlet的

## Servlet线程安全
- 对于实现了SingleThreadModel接口的Servlet，Servlet引擎仍然支持对该Servlet的多线程并发访问，其采用的方式是产生多个Servlet实例对象，并发的每个线程分别调用一个独立的Servlet实例对象

## ServletConfig对象
1. 在Servlet的配置文件中，可以使用一个或多个<init-param>标签为servlet配置一些初始化参数。
2. 当servlet配置了初始化参数后，web容器在创建servlet实例对象时，会自动将这些初始化参数封装到ServletConfig对象中，并在调用servlet的init方法时，将ServletConfig对象传递给servlet。进而，程序员通过ServletConfig对象就可以得到当前servlet的初始化参数信息。

## ServletContext对象
1. WEB容器在启动时，它会为每个WEB应用程序都创建一个对应的ServletContext对象，它代表当前web应用。
2. ServletConfig对象中维护了ServletContext对象的引用，开发人员在编写servlet时，可以通过ServletConfig.getServletContext方法获得ServletContext对象。
3. 由于一个WEB应用中的所有Servlet共享同一个ServletContext对象，因此Servlet对象之间可以通过ServletContext对象来实现通讯。ServletContext对象通常也被称之为context域对象。

## Servlet3.0
1. Servlet3.0是Java EE6规范的一部分，Servlet3.0提供了注解(annotation)，使得不再需要在web.xml文件中进行Servlet的部署描述，简化开发流程。
2. JDK:JDK 1.6+
tomcat：tomcat 7+
3. [annotation-examples](http://www.codejava.net/java-ee/servlet/webinitparam-annotation-examples)
4. @WebServlet注解的相关属性
	- NO.	属性名	描述
	- 1	asyncSupported	声明Servlet是否支持异步操作模式
	- 2	description	Servlet的描述信息
	- 3	displayName	Servlet的显示名称
	- 4	initParams	Servlet的初始化参数
	- 5	name	Servlet的名称
	- 6	urlPatterns	Servlet的访问URL
	- 7	value	Servlet的访问URL

## ServletRequest与ServletResponse对象
- Web服务器收到客户端的http请求，会针对每一次请求，分别创建一个用于代表请求的request对象、和代表响应的response对象。request和response对象即然代表请求和响应，那我们要获取客户机提交过来的数据，只需要找request对象就行了。要向客户机输出数据，只需要找response对象就行了。
- 使用时查看API文档

## 参考
- [孤傲苍狼sevlet](http://www.cnblogs.com/xdp-gacl/p/3760336.html)
