# Tomcat启动时的参数传递

## java -D & java.lang.System

通过java命令启动程序时，-D配置的属性值，将被放在java.lang.System（可以理解为程序的运营环境）。

运行中的程序可以直接通过System.getProperty\(\)，获取-D配置的属性值。

同理

Tomcat启动后，也会将catalina.properties文件里的内容放入System中。

