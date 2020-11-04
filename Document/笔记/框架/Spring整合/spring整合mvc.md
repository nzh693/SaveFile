##### 1. 新增监听器配置

######   **web.xml中设置设置类路径**

```xml

<!--spring监听器，默认加载web-inf文件下的applicationContext.xml-->
<listener>
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
<!--设置配置文件类路径-->
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>classpath:Bean.xml</param-value>
</context-param>
```



##### **2. 开启注解扫描**

```xml
<context:component-scan base-package="controls,service" ></context:component-scan>
```