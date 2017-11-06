## Catalina实例

Thread.currentThread\(\).setContextClassLoader\(catalinaLoader\);

SecurityClassLoad.securityClassLoad\(catalinaLoader\);

catalinaLoader加载org.apache.catalina.startup.Catalina类

实例化一个Catalina

设置该Catalina实例的parentClassLoader为sharedLoader

