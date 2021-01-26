# 目录

- [功能](#功能)
- [效果展示](#效果展示)
- [配置](#配置)

# 功能

- 支持集群状态下的集群监控
- 支持 Spring Boot 自动配置
- 支持 eureka, consul, nacos 三种配置中心

# 效果展示

- 微服务实例页面

  <img src="docs/lib/services.png" width="640" height="770">
  
  `丑是丑了点，原谅一个 Java 后端没啥审美。`

- 首页
  
  <img src="docs/lib/druid-index.png" width="863" height="340">
  
- 数据源
  
  <img src="docs/lib/druid-datasource.png" width="862" height="468">
  
- SQL 监控
  
  <img src="docs/lib/druid-sql.png" width="862" height="295">

# 配置

1. pom.xml 中添加仓库


```xml
<repositories>
    <repository>
        <id>eastsoft-snapshots</id>
        <name>Eastsoft Snapshots</name>
        <url>http://218.58.62.115:18081/nexus/repository/snapshots/</url>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </repository>
</repositories>
```

2. pom.xml 中引入依赖

```xml
<dependency>
    <groupId>com.stark</groupId>
    <artifactId>druid-admin-spring-boot-starter</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>
```

3. yaml 中配置，以 eureka 注册中心为例

```yml
spring:
  datasource:
    druid:
      admin:
        login-username: user
        login-password: 123456
        applications:
        - escloud-service-elk
        - escloud-service-manager
        - escloud-service-ocr
        - escloud-service-user

eureka:
  instance:
    prefer-ip-address: true
    lease-renewal-interval-in-seconds: 5
    lease-expiration-duration-in-seconds: 15
  client:
    service-url:
      defaultZone: http://192.168.22.146:7001/eureka
```

4. 访问 uri `/druid/service.html`
