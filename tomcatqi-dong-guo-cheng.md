## Catalina实例

Bootstrap\#init\(\)的主要功能：

`创建Tomcat的三个ClassLoader`

`Thread.currentThread().setContextClassLoader(catalinaLoader);`

`SecurityClassLoad.securityClassLoad(catalinaLoader);`

`catalinaLoader加载org.apache.catalina.startup.Catalina类`

`实例化一个Catalina`

`设置该Catalina实例的parentClassLoader为sharedLoader`

## Bootstrap与Catalina的关系

Bootstrap创建了Catalina实例，并且充当其代理。例如Bootstrap\#load\(\)方法内部调用的就是Catalina\#load\(\)方法。

## start参数背后的操作

`initDirs();`

`initNaming(); // Before digester - it may be needed`

conf/server.xml

