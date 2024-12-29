---
title: 微服务 集成Open-Feign实现远程方法调用
date: 2021/10/05 15:16:56
update: 2021/10/05
tags:
  - Tag
categories:
- [AlibabaCloud]
---

# Feign让方法调用更加解耦

# 使用feign步骤讲解

1. 加入依赖
```java
<dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-starter-openfeign</artifactId>
</dependency>
```
2. 配置注解
```java
启动类增加@EnableFeignClients
```
3. 增加一个接口
```java
订单服务增加接口，服务名称记得和nacos保持一样
@FeignClient(name="xdclass-video-service") 
```
4. 编写代码
```java
@GetMapping(value = "/api/v1/video/find_by_id")
Video findById(@RequestParam("videoId") int videoId);
```