1.使用idea 创建一个Maven新工程
2.在主工程下新建Eureka Module
3.选择Spring Initializr，然后点击Next
4.输入Module相关信息
5.选中Cloud Discovery，右边勾选Eureka Server
6.然后一路直接到Finish创建完成。
7.pom.xml文件配置
```java
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.yezc.demo</groupId>
    <artifactId>springcloud-eureka</artifactId>
    <version>1.0-SNAPSHOT</version>
    <name>springcloud-eureka</name>

    <parent>
        <groupId>com.yezc.demo</groupId>
        <artifactId>springcloud-demo</artifactId>
        <version>1.0-SNAPSHOT</version>
    </parent>

    <dependencies>
        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-netflix-eureka-server</artifactId>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```
8.在src/main/目录下创建一个包com.yezc.springcloud,然后在包下创建一个启动类
SpringcloudApplication,并且在启动类上添加一个@EnableEurekaServer注解
9.在resources下创建一个application.yml，添加配置如下：
```java
server:
  port: 8001
spring:
  application:
    name: springcloud-eureka
eureka:
  instance:
    hostname: localhost
  client:
    fetch-registry: false
    register-with-eureka: false
  server:
    enable-self-preservation: false
```
10.启动SpringcloudApplication类，浏览器输入http://localhost:8001
可以看到Eureka注册中心的界面
