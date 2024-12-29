---
title: 新一代微服务架构AlibabaCloud全家桶介绍
date: 2021/10/04 12:13:48
update: 2021/11/04
tags:
  - Tag
categories:
- AlibabaCloud
---

# 官网介绍
https://spring.io/projects/spring-cloud-alibaba#overview
 

# 为什么要选择AlibabaCloud , 和SpringCloud的区别
1. SpringCloud和AlibabaCloud组件存在很大交集，互相配合
2. SpringCloud很多组件是基于第三方整合，目前多个已经不更新了，比如zuul、eureka、hystrix等
3. AlibabaCloud 提供一站式微服务解决方法，已经和SpringCloud进行了整合，组件互相支持

# AlibabaCloud全家桶介绍
1. https://github.com/alibaba/spring-cloud-alibaba
2. 服务注册发现：Nacos
3. 服务限流降级：Sentinel
4. 分布配置中心：Nacos
5. 服务网关：SpringCloud Gateway
6. 服务之间调用：Feign、Ribbon
7. 链路追踪：Sleuth+Zipkin
 

# 版本说明
Spring5以上
SpringBoot2.x以上
AlibabaCloud 版本 2.2.x https://spring.io/projects/spring-cloud-alibaba#learn
SpirngCloud版本 Hoxton https://spring.io/projects/spring-cloud

|Release Train	|Boot Version |
|  :----:     | :----:  |
|Hoxton	|2.2.x, 2.3.x (Starting with SR5)|
|Greenwich|	2.1.x|
|Finchley|	2.0.x|
|Edgware|	1.5.x|
|Dalston|	1.5.x|