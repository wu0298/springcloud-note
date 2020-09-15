# 创建common子工程

## 创建maven工程

## 引入pom

```xml
    <dependencies>
        <dependency>
            <groupId>cn.hutool</groupId>
            <artifactId>hutool-all</artifactId>
            <version>5.1.0</version>
        </dependency>
    </dependencies>
```

公共类我们在maven中执行clean，然后再执行install  
之后我们便可以在其他的子模块中的ponm引入公共类的资源  
使用pom引入
```xml
        <dependency>
            <groupId>${公共类的groupId}</groupId>
            <artifactId>${公共类的artifactId}</artifactId>
            <version>${版本编号}</version>
        </dependency>
```

## 创建实体类

```java
//此实体类用来返回给前端接受的json格式
public class CommonResult<T> {
    private Integer code;
    private String message;
    private T      data;

    public Integer getCode() {
        return code;
    }

    public void setCode(Integer code) {
        this.code = code;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }

    public CommonResult() {
    }

    public CommonResult(Integer code, String message) {
        this.code = code;
        this.message = message;
        this.data = null;
    }

    public CommonResult(Integer code, String message, T data) {
        this.code = code;
        this.message = message;
        this.data = data;
    }
}
```

payment 实体类

```Java
package com.study.entity;

/**
 * @author ZIKOR
 * @date 2020/9/14 19:39
 * @desc
 */
public class Payment {

    private long id;
    private String serial;

    public Payment() {
    }

    public Payment(long id, String serial) {
        this.id = id;
        this.serial = serial;
    }

    public long getId() {
        return id;
    }

    public void setId(long id) {
        this.id = id;
    }

    public String getSerial() {
        return serial;
    }

    public void setSerial(String serial) {
        this.serial = serial;
    }
}
```