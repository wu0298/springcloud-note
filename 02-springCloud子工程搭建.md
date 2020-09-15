# 子工程的搭建

在父工程文件上new module创建maven项目

然后创建项目结构创建springboot的启动项

```java
@SpringBootApplication
public class 启动类 {
    public static void main(String[] args) {
        SpringApplication.run(启动类.class, args);
    }
}

```