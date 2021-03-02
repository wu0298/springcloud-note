# 自定义ribbon规则

首先得注意：ribbon规则不能与主启动类在同一个包下

新建一个包，写代码

```java
@Configuration
public class MySelfRule {

    @Bean
    public IRule myRule(){
        return new RandomRule();
    }
}

```

在主启动类增加注解@RibbonClient

```java
@SpringBootApplication
@EnableEurekaClient
@RibbonClient(name = "CLOUD-PAYMENT-SERVICE", configuration = MySelfRule.class)
public class OrderMain8001 {
    public static void main(String[] args) {
        SpringApplication.run(OrderMain8001.class, args);
    }
}
```