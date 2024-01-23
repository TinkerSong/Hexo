---
title: Java核⼼字符串String进阶
date: 2021/09/30 20:02:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 字符串对象String
1. 字符串是对象，不是简单数据类型
2. 封装在java.lang包，⾃动导⼊

# 创建字符串对象
常⻅创建⼀个字符串对象“xdclass.net” ⽅法有下⾯两个
1. String str= new String("xdclass.net");
2. String str= “xdclass.net”

# 字符串⽐较内容是否相等
1. == 是⽐较地址
2. 内容是否相等需要⽤ equals()⽅法⽐较

# 常⻅API
```java
String str = "⼩滴课堂xdclass.net"
 //获取字符串⻓度:
 str.length();

 //通过下标获取字符：
 char char = str.charAt(5);

 //字符串⽐较：
 boolean result = str1.equals(str2);

 //字符串⽐较忽略⼤⼩写
 boolean result = str1.equals(str2);

 //查找字符串出现的位置
 int index = str.indexOf(".");

 //字符串截取
 String result1 = str.substring(index)；
 String result2 = str.substring(index1, index2)；
 //字符串拆分 ,注意正则，可以先简单知道
 String [] arr = str.split("\\.");
 //字符串替换
 str.replace("x","a");

 //字符串⼤⼩写转换
 str.toUpperCase();
 str.toLowerCase();
 //字符串去除空格
 str1.trim();
 ```

# 其他类型和字符串互相转换
```java
boolean bool = Boolean.getBoolean("false"); //字符串类型转换为布尔类型
int integer = Integer.parseInt("20"); //字符串类型转换为整形
long LongInt = Long.parseLong("1024"); //字符串类型转换为⻓整形
float f = Float.parseFloat("1.521"); //字符串类型转换为单精度浮点型
double d = Double.parseDouble("1.52123");//字符串类型转换为双精度浮点型
```
