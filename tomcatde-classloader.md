# Tomcat的ClassLoader

Tomcat启动后初始化了三个ClassLoader，commonLoader、catalinaLoader、sharedLoader。

## parentClassLoader

commonLoader没有parent

catalinaLoader和sharedLoader的parent loader都是commonLoader

## catalina.properties文件

| class loader | catalina.properties文件 |  |
| :--- | :--- | :--- |
| commonLoader | common.loader=“xxxxx” |  |
| catalinaLoader | server.loader= | 如果server.loader配置是空，则catalianLoader就是commonLoader |
| sharedLoader | shared.loader= | 如果shared.loader配置是空，则sharedLoader就是commonLoader |



