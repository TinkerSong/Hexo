---
title: Java核⼼基础之Switch条件分⽀语句
date: 2021/09/3 20:24:00
tags:
  - Tag
categories:
  - Java
---

# 条件语句 switch case ,根据分⽀执⾏对应的逻辑
格式如下
```java
switch(表达式){
 case 表达式常量1:语句1;
 break;
 case 表达式常量2:语句2;
 break;

 ...

 //可以有任意数量的case语句
 case 表达式常量n:语句n;
 break;

 default : //可选
 //语句
}
```
:::info
Switch和if语句都是Java的选择语句，这两种都是允许在程序运⾏时控制程序的执⾏过程。
switch 语句可以拥有多个 case 语句，每个 case 后⾯跟⼀个常量和冒号
default就是如果没有符合的case 就执⾏它,default并不是必须的。
当遇到break语句时，switch语句终⽌。程序跳转到switch语句后⾯的语句执⾏
case语句不必须包含break语句, 没有break语句，程序会执⾏下⼀条case语句，直到出现break语句为⽌
:::
# jdk7之前 switch的case语句⽀持int，short，byte，char类型的值，jdk7后⽀持String类型
```java
int value = 1;
 String day;
 switch (value) {
 case 1: day = "周⼀";
 break;
 case 2: day = "周⼆";
 break;
 case 3: day = "周三"; 
 break;
 case 4: day = "周四";
 break;
 case 5: day = "周五";
 break;
 default: day = "Invalid month";
 break;
 }
 System.out.println(day);
 ```
 :::info
 选择问题：如果只是简单的选择语句 if else即可，复杂或者条件超过4个，则⽤switch语句
 :::
