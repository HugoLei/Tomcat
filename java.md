# Java背景知识

## 为什么程序的入口都是main方法？

C、Java等程序的入口都是main方法，之所以这么统一，其实是约定俗成。

我们写的程序要运行，都有一个初始的执行点（简单理解就是第一句要执行的程序），而这个执行点是被操作系统调用的，为了简化和统一，操作系统只认main方法这个初始执行点。

根据这个约定，其他编程语言的程序入口也大都是main方法。

## Java命令

执行一个class文件，可通过命令行的java的命令，例如java HelloWorld。

java命令会启动JVM（？？？）

JVM启动入口（？？？）

## Java自身的ClassLoader

自带3个ClassLoader，如下。

### **BootstrapClassLoader**

最顶层的加载类，主要`加载核心类库`，%JRE\_HOME%\lib下的rt.jar、resources.jar、charsets.jar和class等。

另外需要注意的是可以通过启动jvm时指定-Xbootclasspath和路径来改变Bootstrap ClassLoader的加载目录。比如

`java -Xbootclasspath/a:path`被指定的文件追加到默认的bootstrap路径中。

我们可以打开我的电脑，在上面的目录下查看，看看这些jar包是不是存在于这个目录。

### ExtClassLoader

扩展的类加载器，加载目录%JRE\_HOME%\lib\ext目录下的jar包和class文件。

还可以加载`-D java.ext.dirs`选项指定的目录。

### AppClassLoader

加载当前应用的classpath的所有类。

> **总结：不同的类加载器，加载的是不同路径**

| **BootstrapClassLoader** | **`sun.boot.class.path`** | 核心类库 |
| :--- | :--- | :--- |
| **ExtClassLoader** | **`java.ext.dirs`** | **扩展类库** |
| **AppClassLoader** | **`java.class.path`** | **当前应用的类库** |



