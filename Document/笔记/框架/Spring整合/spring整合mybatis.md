##### <u>新增依赖</u>

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>5.1.5.RELEASE</version>
</dependency>
```



```xml
<!--阿里巴巴连接池-->
<!-- https://mvnrepository.com/artifact/com.alibaba/druid -->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.1.4</version>
</dependency>
```

##### 1. 导入外部配置文件

（.properties）

​	

```xml
<bean class="org.springframework.beans.factory.config.PropertyPlaceholderConfigurer">
         <property name="location" value="classpath:database.properties"/>
     </bean>
```



##### 2. 配置数据源

​	Druid 连接池子 最牛皮的池子

```xml
    <!--2. 配置数据源-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init"
          destroy-method="close">
        <property name="driverClassName" value="${driver}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${name}"/>
        <property name="password" value="${password}"/>
    </bean>
```



##### 3. 配置sqlSessionFactory

​	

```xml
 <!--3. 配置sqlSessionFactory-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <!--引用数据源-->
        <property name="dataSource" ref="dataSource"></property>
        <!--mybstis配置文件-->
        <property name="configLocation" value="classpath:MyBatisConfig.xml"></property>
    </bean>
```



##### 4. 配置SQL映射

```xml
<!--4. 配置SQL映射   dao:包名-->
<bean id="MapperScanner" class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <property name="basePackage" value="dao"></property>
</bean>
```





