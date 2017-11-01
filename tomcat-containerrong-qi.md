# Tomcat管理Servlet的Container容器

## 概述

Container包含4层容器

顶层容器是：Engine引擎，只有一个，负责多个站点

Host代表站点（虚拟主机），一个Engine包含多个Host

Context代表一个应用，一个Host有多个Context

Wrapper代表一个Servlet，一个Context包含多个Wrapper

  


Context vs. Host

Context表示应用（多个Context）

如webapps/ROOT目录，对应ROOT主应用

如webapps/uncle目录，对应uncle应用

  


  


  


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

  


  


