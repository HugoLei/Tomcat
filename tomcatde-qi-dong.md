# Tomcat的启动命令

## Tomcat本身也是个Java程序，那这个程序的入口在哪里呢？

在org.apache.catalina.startup.Bootstrap 的main\(String\[\] args\)里（是不是很熟悉main方法）。

这个main方法在lib/catalina.jar这个包里。

## 那如何启动jar包里的main方法呢？

来看下Tomcat的启动命令，startup.sh，这里面会调用catalina.sh执行具体的动作，catalina.sh最终会调用如下命令：

`/home/work/app/.jdk/bin/java`

`-Djava.util.logging.config.file=/home/work/conf/logging.properties`

`-Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager`

``-server`**``// server模式启动比client慢，但可获得更高的运行性能\`\*\*

`-verbose:gc`

`-Xloggc:/home/work/jpaas_run/logs/gc.log`

`-XX:+PrintGCTimeStamps`

`-XX:+PrintGCDetails`

`-Djava.awt.headless=true`

`-Xmx1792m -Xms1792m -XX:PermSize=256m -XX:MaxPermSize=256m`

`-Duser.timezone=GMT+08`

`-javaagent:/home/work/.jvmagent/jvmagent.jar`

`-Dport.http.nonssl=8080`

`-Djava.endorsed.dirs=/home/work/endorsed`

`-classpath /home/work/bin/bootstrap.jar // 指明搜索路径，设置后不按CLASSPATH环境变量去搜索`

`-Dcatalina.base=/home/work`

`-Dcatalina.home=/home/work`

`-Djava.io.tmpdir=/home/work/temp`

`org.apache.catalina.startup.Bootstrap start`

**简版的启动命令是：java org.apache.catalina.startup.Bootstrap start**

**main方法在Bootstrap类中，Bootstrap类在包org.apache.catalina.startup里，start是运行参数**

