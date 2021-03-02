# 修改名称

未修改时我们的名称

```
ZIKOR.mshome.net:cloud-payment-service:8081 , ZIKOR.mshome.net:cloud-payment-service:8082
```

主机名被暴露

我们在支付模块的yml配置中添加

```yml
eureka:
  client:
    register-with-eureka: true #false表示不向注册中心注册自己
    fetch-registry: true #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    service-url:
      #设置与Eureka Server交互的地址查询服务和注册服务都需要依赖这个地址
#      defaultZone: http://localhost:7001/eureka
      defaultZone: http://localhost:7001/eureka,http://localhost:7003/eureka
  instance:
    instance-id: payment8081
    prefer-ip-address: true  #访问路径可以显示IP地址
```

eureka.instance.instance-id: payment8081

这样修改后在我们的eureka中将会显示payment8081

> payment8081 , payment8082

prefer-ip-address: true  #访问路径可以显示IP地址

添加后我们将鼠标放在payment8081上可以显示IP地址