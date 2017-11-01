# Tomcat上层容器

## Server

最顶层的容器是Server，代表整个Tomcat服务器。一个Tomcat只有一个Server。



## Service

Service用于提供服务，Server包含多个Service。



## Connector & Container

Service主要包含两部分：Connector 和 Container

Connector负责处理请求连接（核心功能一）

Container负责管理Servlet（核心功能二）

Service包含

多个Connector

对应不同类型的链接，如HTTP，HTTPS，APR等

对应不同端口的链接，如HTTP8080，HTTP8081端口等

Service包含

1个Container

