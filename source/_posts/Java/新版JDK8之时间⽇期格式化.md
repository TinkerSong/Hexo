---
title: 新版JDK8之时间⽇期格式化
date: 2021/09/28 19:43:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 为什么要时间⽇期做格式化
程序打印，或者⽹⻚显示时间⽇期格式，⽤户有不同的需求，则需要根据⼀定的规则进⾏格式化

# 常⽤的占位符
:::info
y　　四位数年份
M　　⽉
d　　⽇
h　　时 在上午或下午 (1~12)
H　　时 在⼀天中 (0~23)
m　　分
s　　秒
S　　毫秒
:::

# JDK8之后：引⼊线程安全的⽇期与时间DateTimeFormatter
```java
LocalDateTime ldt = LocalDateTime.now();
System.out.println(ldt);
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd
HH:mm:ss");
String ldtStr = dtf.format(ldt);
System.out.println(ldtStr);
```
# 获取指定的⽇期时间对象 
```java
LocalDateTime ldt = LocalDateTime.of(2020, 11, 11, 8, 20, 30);
System.out.println(ldt);
```

# 计算⽇期时间差 java.time.Duration
```java
LocalDateTime today = LocalDateTime.now();
 System.out.println(today);
 LocalDateTime changeDate = LocalDateTime.of(2020,10,1,10,40,30);
 System.out.println(changeDate);
 Duration duration = Duration.between( today,changeDate);//第⼆个参数减第⼀
个参数
 System.out.println(duration.toDays());//两个时间差的天数
 System.out.println(duration.toHours());//两个时间差的⼩时数
 System.out.println(duration.toMinutes());//两个时间差的分钟数
 System.out.println(duration.toMillis());//两个时间差的毫秒数
 System.out.println(duration.toNanos());//两个时间差的纳秒数
 ```