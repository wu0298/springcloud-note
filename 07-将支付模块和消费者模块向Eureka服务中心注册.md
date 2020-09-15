# 服务中心注册支付模块

在支付模块的pom中引入eureka-client依赖

```xml
        <!-- 引入eureka依赖-->
        <!-- https://mvnrepository.com/artifact/org.springframework.cloud/spring-cloud-starter-netflix-eureka-server -->
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
        </dependency>
```

在yml添加eureka配置

```yml
eureka:
  client:
    register-with-eureka: true #false表示不向注册中心注册自己
    fetch-registry: true #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    service-url:
      #设置与Eureka Server交互的地址查询服务和注册服务都需要依赖这个地址
      defaultZone: http://localhost:7001/eureka
```

```yml
spring:
  application:
    name: cloud-payment-service #这个名称是向服务中心注册时所使用的名称
```

在启动类添加注解@EnableEurekaClient

```java
@SpringBootApplication
@EnableEurekaClient
public class PaymentMain8081 {
    public static void main(String[] args) {
        SpringApplication.run(PaymentMain8081.class, args);
    }
}

```

同样的方法将消费者注册