---
title: Java⽇期处理类Date详解
date: 2021/09/25 22:12:00
tags:
  - Tag
categories:
  - Java
---

# 时间的基础知识
:::info
时区：整个地球分为⼆⼗四时区，每个时区都有⾃⼰的本地时间。
为了统⼀起⻅，使⽤⼀个统⼀的时间，称为全球标准时间(UTC, Universal Time
Coordinated)。
TC与格林尼治平均时(GMT, Greenwich Mean Time，也翻译成：格林威治标准时间)差不多⼀
样
CST(北京时间)，北京时间，China Standard Time，中国标准时间。在时区划分上，属东⼋
区，⽐协调世界时早8⼩时，记为UTC+8。
时间戳：⾃ 1970 年 1 ⽉ 1 ⽇（08:00:00 GMT）⾄当前时间的总秒数，它也被称为Unix时
间戳（Unix Timestamp），⼴泛的运⽤在知识产权保护、 合同签字、 ⾦融帐务、 电⼦报价投
标、 股票交易等⽅⾯
格式多种：2050-10-31 10:11:11、2050/10/31 10/10:10
年、⽉、⽇、周⼏等
:::

# 背景:
1. 程序代码中怎么表示时间呢？我需要获取当前时间怎么办
2. java.util包提供了Date类来封装当前的⽇期和时间

# 构造函数
```java
//当前时间
Date()
//从1970年1⽉1⽇起的毫秒数作为参数
Date(long millisec)
```

# 常⻅⽅法
```java
//返回⾃ 1970 年 1 ⽉ 1 ⽇ 00:00:00 GMT 以来此 Date 对象表示的毫秒数。
long getTime( )
//调⽤此⽅法的Date对象在指定⽇期之后返回true,否则返回false。
boolean after(Date date)
//调⽤此⽅法的Date对象在指定⽇期之前返回true,否则返回false。
boolean before(Date date)
```