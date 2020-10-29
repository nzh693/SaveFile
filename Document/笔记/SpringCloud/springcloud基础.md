### SpringCloud Alibaba

####  一、简介

​          Spring Cloud  Alibaba 致力于提供微服务开发的一站式解决方案，此项目包含开发分布式应用微服务的必要组件，方便开发者通过Spring Cloud 编程模拟轻松使用这些组件来开发分布式应用服务。依托于这个，只需要添加少量的注解和配置，就可以将Spring Cloud 应用接入阿里微服务解决方案，通过阿里中间件来迅速搭建分布式应用系统。

#### 二、 Sentinel

​          把流量作为切入点，从控制流量、熔断降级、系统负载保护等多个维度保护服务的稳定性。

#### 三、 Nacos

​           一个更易于构建云原生应用的动态服务发现、管理配置和服务管理平台。

##### 3.1 注册中心

​       需求：注册发现服务，便于远程调用服务。[官方使用说明](https://github.com/alibaba/spring-cloud-alibaba/blob/master/spring-cloud-alibaba-examples/nacos-example/nacos-discovery-example/readme-zh.md)

##### 3.2 配置中心

​      需求：动态更改微服务的配置项，无需更改原码以及重新打包部署。     

​      **基本使用**

​      引入依赖：

```xml
<!--配置中心-->
<dependency>
    <groupId>com.alibaba.cloud</groupId>
    <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
    <version>2.2.1.RELEASE</version>
</dependency>
```

 在yml中配置服务名称和配置中心地址，在nacos控制中心添加配置DataID为服务名+”.properties“

```yml
cloud: 
  #服务的注册和发现
  nacos:
    discovery:
      server-addr: 127.0.0.1:8848
    config:
      refresh-enabled: true
      server-addr: 127.0.0.1:8848
application:
  name: hrrecruit
```

 在使用配置的类上加注解**@RefreshScope**，从配置文件中加载配配置 【**@Value**("${xxx}")注解】。

```java
@RestController
@RefreshScope
@RequestMapping("/recruit")
public class TestController {
    @Autowired
    private FeignApi feignApi;

    @Value("${recruit.name}")
    private String name;

    /**
     * 测试远程调用
     * @return
     */
    @RequestMapping("testFeign")
    public String testFeign(){
        System.out.println("测试远程服务");
        String re = feignApi.TestFeign();
        return "测试远程调用："+re;
    }

    /**
     * 测试配置中心
     * @return
     */
    @RequestMapping("testConfig")
    public String testConfig(){
        System.out.println("测试配置中心");
        return "测试配置中心："+name;
    }

}
```

**命名空间**：一般用于配置隔离。默认所有新增的配置都在public空间。比如：测试环境、开发环境、生产环境。

​     每一个微服务之间互相隔离配置，每一个微服务都创建自己的命令空间，只加载自己的命名空间下的所有配置；



##### 3.3 远程调用 Feign 

​     需求：服务之间的调用

​     **基本使用deom**

​     引入依赖

```xml
<!--服务的调用-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-openfeign</artifactId>
    <version>2.2.2.RELEASE</version>
</dependency>
```

构建一个服务的远程调用接口，并添加**@FeignClient**注解。

```JAVA
@FeignClient("hrsalary") //远程被调用的服务注册名称
public interface FeignApi {
    //远程调用服务的接口全路径 
    //ps：方法签名要完全与被调用的接口保持一致
    @RequestMapping("/salary/get")
    public String TestFeign();

}
```

在启动类上添加**@EnableFeignClients**(basePackages = "com.hr.recruit.recruit.feign") 扫描远程调用的接口包。以上步骤完成后就可以按照接口进行远程调用





#### 四、 RocketMQ

​         开源的分布式消息系统，基于高可用分布式集群技术，提供低延迟的高可靠的消息发布于订阅服务。

#### 五、 Dubbo

​         Apache Dubbo 是一款高性能的Java RPC框架。

#### 六、 Seata

​        阿里巴巴开源产品，一个易于使用的高性能微服务分布式事物解决方案。

#### 七、 Alibaba Cloud ACM 

​        一款子在分布式架构环境中对应用配置进行集中管理和推送的应用配置中心产品。

#### 八、 Alibaba Cloud OSS

​       阿里云对象存储服务(Object Storage Service) 简称OSS，阿里云提供的海量、安全、低成本、高可靠的云存储服务，在任何应用、时间、地点存储和访问任意类型的数据。

#### 九、 Alibaba Cloud SchedulerX

​       阿里中间件团队开发的一款分布式任务调度，提供秒级、精准、高可靠、高可用的定时调度任务(基于corn表达式)

#### 10、 Alibaba Cloud SMS

​      覆盖全球的短信服务，友好、高效、智能的互联化通讯能力，帮助企业迅速搭建客户触达通道。



