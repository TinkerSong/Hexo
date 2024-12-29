---
title: Objects⼯具类重点⽅法使⽤
date: 2021/09/18 21:14:00
tags:
  - Tag
categories:
  - Java
---

# Objects⼯具类讲解
1. jdk1.7引进的⼯具类，都是静态调⽤的⽅法，jdk1.8新增了部分⽅法
2. 重点⽅法
:::info
equals
⽤于字符串和包装对象的⽐较，先⽐较内存地址，再⽐较值

deepEquals
数组的⽐较，先⽐较内存地址，再⽐较值，如String/char/byte/int数组， 或者包装类型Integer等数组

hashCode
返回对象的hashCode，若传⼊的为null，返回0

hash
传⼊可变参数的所有值的hashCode的总和，底层调⽤Arrays.hashCode
:::

# 可变参数(只能在最后⼀个参数⾥⾯加)
```java
public static int hash(Object... values) {
 return Arrays.hashCode(values);
 }
 ```