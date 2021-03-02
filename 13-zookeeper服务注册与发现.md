# zookeeper服务注册与发现

pom依赖

```xml
    <dependencies>
        <!-- 引入zookeeper客户端  -->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-zookeeper-discovery</artifactId>
        </dependency>
        <!-- 引入自定义公共包 -->
        <dependency>
            <groupId>com.study</groupId>
            <artifactId>cloud-api-commons</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!--spring boot 2.2.2-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
        </dependency>
        <!--spring cloud Hoxton.SR1-->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-dependencies</artifactId>
        </dependency>
        <!--spring cloud alibaba-->
        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-alibaba-dependencies</artifactId>
        </dependency>

        <!--log4j-->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
        </dependency>
    </dependencies>
```

配置文件

```yml
#8084表示注册到zookeeper服务器的支付服务提供者端口号
server:
  port: 8001


# 服务别名----注册zookeeper到注册中心名称
spring:
  application:
    name: cloud-consumner-order
  cloud:
    zookeeper:
      #注册到zookeeper地址
      connect-string: 服务器地址:端口号
      #connect-string: 服务器地址:端口号,服务器地址:端口号 #集群
```

可以在zookeeper中的services中查看到注册的信息。