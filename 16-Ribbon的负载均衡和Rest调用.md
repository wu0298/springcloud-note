# Ribbon的负载均衡和Rest调用

新版本的Eureka已经默认集成了Ribbon，不需要我们进行pom引用

Ribbon实现了本地的负载均衡

通俗理解就是在注册中心注册了ribbon，当我们请求调用的时候，  
ribbon自动通过服务中心选择一个空闲的服务来调用请求。

RestTempalte调用： 见名知意 如:getForObject和postForObject(get和post请求)