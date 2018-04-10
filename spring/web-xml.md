---
title: 2018-04-09-web.xml配置详解
date:  2018-04-09 12:04:02
categories:
- spring 
tags:
- web 
---

### web.xml配置文件常用配置及其意义预览

> [web.xml配置详解](https://www.cnblogs.com/hafiz/p/5715523.html)

```
 1 <web-app>
 2 
 3      <!--定义了WEB应用的名字-->
 4      <display-name></display-name>
 5 
 6      <!--声明WEB应用的描述信息-->
 7      <description></description>
 8 
 9      <!--context-param元素声明应用范围内的初始化参数-->
10      <context-param></context-param>
11 
12      <!--过滤器元素将一个名字与一个实现javax.servlet.Filter接口的类相关联-->
13      <filter></filter>
14 
15      <!--一旦命名了一个过滤器，就要利用filter-mapping元素把它与一个或多个servlet或JSP页面相关联-->
16      <filter-mapping></filter-mapping>
17 
18      <!--servlet API的版本2.3增加了对事件监听程序的支持，事件监听程序在建立、修改和删除会话或servlet环境时得到通知。
19          Listener元素指出事件监听程序类-->
20      <listener></listener>
21 
22      <!--在向servlet或JSP页面制定初始化参数或定制URL时，必须首先命名servlet或JSP页面。
23          Servlet元素就是用来完成此项任务的-->
24      <servlet></servlet>
25 
26      <!--服务器一般为servlet提供一个缺省的URL：http://host/webAppPrefix/servlet/ServletName。
27          但是，常常会更改这个URL，以便servlet可以访问初始化参数或更容易地处理相对URL。
28          在更改缺省URL时，使用servlet-mapping元素-->
29      <servlet-mapping></servlet-mapping>
30 
31      <!--如果某个会话在一定时间内未被访问，服务器可以抛弃它以节省内存。可通过使用HttpSession的
32          setMaxInactiveInterval方法明确设置单个会话对象的超时值，或者可利用session-config元素制定缺省超时值-->
33      <session-config></session-config>
34 
35      <!--如果Web应用具有想到特殊的文件，希望能保证给他们分配特定的MIME类型，则mime-mapping元素提供这种保证-->
36      <mime-mapping></mime-mapping>
37 
38      <!--指示服务器在收到引用一个目录名而不是文件名的URL时，使用哪个文件-->
39      <welcome-file-list></welcome-file-list>
40 
41      <!--在返回特定HTTP状态代码时，或者特定类型的异常被抛出时，能够制定将要显示的页面-->
42      <error-page></error-page>
43 
44      <!--对标记库描述符文件（Tag Libraryu Descriptor file）指定别名。此功能使你能够更改TLD文件的位置，
45          而不用编辑使用这些文件的JSP页面-->
46      <taglib></taglib>
47 
48      <!--声明与资源相关的一个管理对象-->
49      <resource-env-ref></resource-env-ref>
50 
51      <!--声明一个资源工厂使用的外部资源-->
52      <resource-ref></resource-ref>
53 
54      <!--制定应该保护的URL。它与login-config元素联合使用-->
55      <security-constraint></security-constraint>
56 
57      <!--指定服务器应该怎样给试图访问受保护页面的用户授权。它与sercurity-constraint元素联合使用-->
58      <login-config></login-config>
59 
60      <!--给出安全角色的一个列表，这些角色将出现在servlet元素内的security-role-ref元素的role-name子元素中。
61          分别地声明角色可使高级IDE处理安全信息更为容易-->
62      <security-role></security-role>
63 
64      <!--声明Web应用的环境项-->
65      <env-entry></env-entry>
66 
67      <!--声明一个EJB的主目录的引用-->
68      <ejb-ref></ejb-ref>
69 
70      <!--声明一个EJB的本地主目录的应用-->
71      <ejb-local-ref></ejb-local-ref>
72 
73  </web-app> 
```
### 重要配置元素详解

1.上下文参数：声明应用范围内的初始化参数
```
1 <context-param>
2      <param-name>参数名</para-name>
3      <param-value>参数值</param-value>
4      <description>参数描述</description>
5  </context-param>
```
在servlet里面可以通过 getServletContext().getInitParameter(“context/param”)得到

2.过滤器配置：将一个名字与一个实现javaxs.servlet.Filter接口的类相关联

```
    <filter>
        <description>字符集过滤器</description>
        <filter-name>encodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <description>字符集编码</description>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
        <init-param>
            <param-name>forceEncoding</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>encodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```

3.会话超时配置（单位为分钟）

```
	<session-config>
		<session-timeout>120</session-timeout>
	</session-config>

```

4.监听器配置

```
    <listener>
        <description>spring监听器</description>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>

```