Oracle/Sun HotSpot VM - 整体都是用C++实现的，只有非常少量的内嵌汇编

.java是源代码文件

.class是编译后机器能够识别的

class load本质就是从.class文件中读取类（操作就是读文件）

Java的类加载器

Bootstrap ClassLoader\(用C++写的\)

ExtClassLoader

AppClassLoader

Tomcat Bootstrap类里创建3个类加载器commonLoader，catalinaLoader，sharedLoader

```
commonLoader = createClassLoader("common", null);
            if( commonLoader == null ) {
                // no config file, default to this loader - we might be in a 'single' env.
                commonLoader=this.getClass().getClassLoader();
            }
            catalinaLoader = createClassLoader("server", commonLoader);
            sharedLoader = createClassLoader("shared", commonLoader);
```

![](/assets/import.png)

这三个都是URLClassLoader（Java里的）

