---
title: Java枚举的常⻅API的使⽤
date: 2021/10/01 13:23:00
tags:
  - Tag
categories:
  - Java
---

# 常⻅API的使⽤
```java
//返回此枚举常量的名称
name()
//该⽅法获取的是枚举变量在枚举类中声明的顺序，下标从0开始（它在枚举声明中的位置，其中
初始常量序数为零,如果枚举的位置发⽣变化，对应的值也会变化）
ordinal()
//和name⽅法⼀样
toString()
```

# 默认⽣成的values⽅法与valueOf⽅法 
```java
//通过字符串获取对应的枚举值 valueOf()
//获取枚举类中的所有变量，并作为数组返回 values()
```

# 例⼦
```java
Day [] days = Day.values();
Day day = Day.valueOf("MONDAY");
System.out.println(day.name());

//枚举类型，使⽤关键字enum
enum Day {
 MONDAY, TUESDAY, WEDNESDAY,
 THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
```