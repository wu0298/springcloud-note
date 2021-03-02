# Feign超时控制和日志增强

## 超时控制

Feign请求资源只有默认一秒钟的时间，如果超过一秒钟的话直接报错，这里就需要我们手动设置

在yml中设置5秒

```yml
ribbon:
  #指的是简历连接后从服务器读取到可用资源所用的时间
  ReadTimeout: 5000
  #指的是建立连接所用的时间，适用于网络状况正常的情况下，两端连接所用的时间
  ConnectTimeout: 5000
```

## 日志增强

NONE: 默认的，不显示任何日志；

BASIC： 仅记录请求方法、URL、响应状态码及执行时间；

HEADERS： 除了BASIC中定义的信息之外，还有请求和响应的头信息；

FULL： 除了HEADERS中定义的信息之外，还有请求和响应的正文及元数据。

配置类中注入日志

```java
@Configuration
public class FeignConfig {
    //Feign.Logger
    @Bean
    Logger.Level feignLoggerLevel(){
        return Logger.Level.FULL;
    }
}
```

在yml中配置

```yml
logging:
  level:
    com.study.service.PaymentService: debug
```