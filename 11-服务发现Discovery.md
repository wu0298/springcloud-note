# 初体验

```java
    @Resource
    private DiscoveryClient discoveryClient;

    @GetMapping("/payment/discovery")
    public Object discovery(){
        List<String> services = discoveryClient.getServices();
        for (String element : services){
            logger.info("****elements: "+element);
        }
        List<ServiceInstance> instances = discoveryClient.getInstances("CLOUD-PAYMENT-SERVICE");
        for (ServiceInstance instance : instances){
            logger.info(instance.getServiceId()+"\t"+instance.getHost()+"\t"+instance.getPort()+"\t"+instance.getUri());
        }

        return this.discoveryClient;
    }
```

调用查看信息：

```log
****elements: cloud-consumer-order
2020-09-18 14:59:34.267  INFO 9312 --- [nio-8081-exec-4] com.study.controller.PaymentController   : ****elements: cloud-payment-service
2020-09-18 14:59:34.268  INFO 9312 --- [nio-8081-exec-4] com.study.controller.PaymentController   : CLOUD-PAYMENT-SERVICE	192.168.137.201	8081	http://192.168.137.201:8081
2020-09-18 14:59:34.268  INFO 9312 --- [nio-8081-exec-4] com.study.controller.PaymentController   : CLOUD-PAYMENT-SERVICE	192.168.137.201	8082	http://192.168.137.201:8082
```