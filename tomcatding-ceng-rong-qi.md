# Tomcat上层容器

## Server

最顶层的容器是Server，代表整个Tomcat服务器。一个Tomcat只有一个Server。

## Service

Service用于提供服务，Server包含多个Service。

Service通过两个部分提供服务：Connector 和 Container

## Connector

Connector负责处理请求连接（核心功能一）

1个Service包含多个Connector

对应不同类型的链接，如HTTP，HTTPS，APR等

对应不同端口的链接，如HTTP8080，HTTP8081端口等

## Container

Container作为容器，负责管理Servlet（核心功能二）

1个Service包含1个Container

