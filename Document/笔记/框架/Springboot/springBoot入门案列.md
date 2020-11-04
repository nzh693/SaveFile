#### 一、idea内部运行

##### 1. 导入依赖

```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.2.4.RELEASE</version>
</parent>


<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```



##### 2. 主程序

```java
@SpringBootApplication
public class MainApplication {
    public static void main(String[] args) {
        SpringApplication.run(MainApplication.class,args);
    }
}
```



##### 3. 控制类

```
@Controller
public class HelloControler {

    @ResponseBody
    @RequestMapping(path = "/hello")
    public String hello(){
        return "hello boot";
    }
}
```





###### 即可直接运行主函数 ==》浏览器发送hello请求  输出结果

![image-20200211184317732](image/image.png)

#### 二、无需部署打包成jar包直接运行

#####         1. 导入插件

​          

```
<!--打包成jar-->
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

#####        2. maven命令package打包 

![image-20200211184743474](C:\Users\NZH\AppData\Roaming\Typora\typora-user-images\image-20200211184743474.png)



##### 		3. java -jar +jar包全限名称 运行

​            浏览器发送hello请求  输出结果相同



from docker.io/tomcat

maintainer nzh_693@163.com

COPY success-0.0.1-SNAPSHOT.war  /usr/local/tomcat/webapps









