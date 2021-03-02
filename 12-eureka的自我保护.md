# eureka的自我保护

当某个微服务不可用了，比如拓机出故障等，eureka不会立刻将其清理，一就会对该服务的信息进行保存

当我们禁止了eureka的自我保护，eureka将会立刻清理这个微服务

开启方法

服务模块(以支付模块为例)

```yml
eureka:
  instance:
    #Eureka客户端向服务端发送心跳的时间间隔，单位为秒(默认30秒)
    lease-renewal-interval-in-seconds: 1
    #Eureka服务端在接收到最后一次心跳后等待时间上限，单位为秒(默认是90秒)，超市将剔除服务
    lease-expiration-duration-in-seconds: 2
```

Eureka服务中心

```yml
eureka:
  instance:
    hostname: eureka7001.com #eureka服务端的实例名称
  client:
    register-with-eureka: false #false表示不向注册中心注册自己
    fetch-registry: false #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    service-url:
      #设置与Eureka Server交互的地址查询服务和注册服务都需要依赖这个地址
      defaultZone: http://eureka7003.com:7003/eureka/
  server:
    #关闭自我保护机制，保证不可用服务被及时剔除
    enable-self-preservation: false
    eviction-interval-timer-in-ms: 2000 #2秒
```