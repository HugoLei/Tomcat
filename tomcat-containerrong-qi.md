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

总结：多Host可以支持多域名

## 为什么Host包含多个Context？

将一个大的工程分成小的模块，每个模块作为一个功能完整的应用，方便开发



## 总结

Tomcat可支持：

* 多端口（如：8001，8080）
* 多协议（如：HTTP，HTTPS）
* 多域名（多站点，多Host实现）



备注：

如果是其他域名，或者IP直接访问，会走Engine配置的defaultHost，如果没有配置这个属性，则访问不了。

同一个Service下的Connector是共享的，所以如果站点只想监听自己独立的端口，需要配置到另一个Service中。

