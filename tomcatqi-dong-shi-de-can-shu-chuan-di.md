# Tomcat启动时的参数传递

## java -D & java.lang.System

通过java命令启动程序时，-D配置的属性值，将被放在java.lang.System（可以理解为程序的运营环境）。

运行中的程序可以直接通过System.getProperty\(\)，获取-D配置的属性值。

## Tomcat & System

Tomcat启动后，也会将catalina.properties文件里的内容放入System中。

举例：catalina.properties文件中的common.loader的配置如下

common.loader=${catalina.base}/lib,${catalina.base}/lib/\*.jar,${catalina.home}/lib,${catalina.home}/lib/\*.jar

代码中是如何解析这个配置的呢？如何获取变量的值？

处理此字符串，匹配${,}符号，然后从System中获取“catalina.base”和“catalina.home”的值

