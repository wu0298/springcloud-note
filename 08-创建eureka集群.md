# 创建集群

使用创建cloud-eureka-server7001同样的方法创建  
cloud-eureka-server7002

在系统中修改C:\Windows\System32\drivers\etc\hotst文件

添加
```
127.0.0.1  eureka7001.com
127.0.0.1  eureka7002.com
127.0.0.1  eureka7003.com
```

将cloud-eureka-server7001的名称改为eureka7001.com(主要作用是用来标识)，同时修改defaultZone地址

```yml
server:
  port: 7001

eureka:
  instance:
    hostname: eureka7001.com #eureka服务端的实例名称
  client:
    register-with-eureka: false #false表示不向注册中心注册自己
    fetch-registry: false #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    service-url:
      #设置与Eureka Server交互的地址查询服务和注册服务都需要依赖这个地址
      defaultZone: http://eureka7003.com:7003/eureka/

```

同样的将cloud-eureka-server7002设置好端口，地址指向eureka7001.com:7001/eureka/

# 将支付模块同时注册两个服务中心

```yml
eureka:
  client:
    register-with-eureka: true #false表示不向注册中心注册自己
    fetch-registry: true #false表示自己端就是注册中心，我的职责就是维护服务实例，并不需要去检索服务
    service-url:
      #设置与Eureka Server交互的地址查询服务和注册服务都需要依赖这个地址
      defaultZone: http://localhost:7001/eureka,http://localhost:7002/eureka
```