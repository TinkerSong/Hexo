---
title: java系统类之System类讲解
date: 2021/09/30 20:32:00
tags:
  - Tag
categories:
  - Java
---

# 什么是System类
1. 位于java.lang包中，它是系统类，代表程序所在系统，提供了对应的⼀些系统属性信息和系统操作
2. final类型，构造函数被私有化

3 常⽤API
```java
//输⼊输出包含三个成员变量，分别是in，out，err
System.out //常⽤调试
System.in //⽤于数据读取，少⽤
System.err //⽤在错误输出，少⽤
//获取系统当前毫秒值
System.currentTimeMillis()
//获取系统环境的属性
System.getProperties()
//根据指定key获取系统属性
System.getProperties(key)
```
