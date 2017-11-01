# Tomcat管理Servlet的Container容器

## 概述

Container包含4层容器，层层包含。

顶层容器是：Engine引擎，只有一个，负责多个站点

Host代表站点（虚拟主机），一个Engine包含多个Host

Context代表一个应用，一个Host有多个Context

Wrapper代表一个Servlet，一个Context包含多个Wrapper



## Context vs. Host

Context表示应用，例如：

1. 如webapps/ROOT目录，对应ROOT主应用
2. 如webapps/uncle目录，对应uncle应用

Host表示站点（可以理解为域名），一个站点可以包含多个应用，例如：

1. 站点www.zoom.com，下面包含“动物”应用，“经费”应用，“访客”应用等
2. 其中www.zoom.com表示站点，“动物”“经费”“访客”等代表不同的应用Context



## 为什么Container包含多个Host？

站点www.zoom.com对应一个Host

如果当前的Tomcat还想处理www.dog.com站点的请求，则需要新建一个Host





理解：

* action就相当于是Servlet
* Context代表一个工程，所以会包含多个Servlet
* www.baidu.com对应一个站点Host，直接访问www.baidu.com进入webapps/ROOT目录的Context，访问www.baidu.com/uncle进入webapps/uncle目录的Context
* 假如还有另外一个域名www.jd.com进入到这个Tomcat，则进入另一个站点Host，继续访问这个Host下的Context
* 多Host可以支持多域名

综述：

从业务访问的角度看，Tomcat可以支持如下的访问：

* 多域名（多站点：多Host）
* 域名下多应用（多Context）
* 多协议，多端口（多Connector，HTTP，HTTPS，APR，8001，8080）

备注：

如果是其他域名，或者IP直接访问，会走Engine配置的defaultHost，如果没有配置这个属性，则访问不了。

同一个Service下的Connector是共享的，所以如果站点只想监听自己独立的端口，需要配置到另一个Service中。

