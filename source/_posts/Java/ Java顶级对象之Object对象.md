---
title:  Java顶级对象之Object对象
date: 2021/09/29 21:12:00
tags:
  - Tag
categories:
  - Java
---

# 什么是Object类
1. Object类位于java.lang包中，java.lang包包含着Java最基础和核⼼的类，在编译时会⾃动导⼊
2. Object类是所有Java类的祖先,每个类都使⽤ Object 作为超类

# 常⻅⽅法
```java
public final native Class<?> getClass()
//讲解：获取对象的运⾏时class对象，class对象就是描述对象所属类的对象, 类的对象可以获取这个类的基本信息，如名、包、字段、⽅法等（⽤于反射会⽐较多，以后有机会再了解）
public native int hashCode()
//讲解：获取对象的散列值，集合框架中应⽤，⽐如HashMap
public boolean equals(Object obj)
//讲解：⽐较两个对象，如果这两个对象引⽤指向的是同⼀个对象，那么返回true，否则返回false集合框架中有讲
public String toString()
//讲解：⽤于返回⼀个可代表对象的字符串，看源码可以得知，默认返回格式如下：对象的class名称 +
@ + hashCode的⼗六进制字符串,所以前⾯课程写对象时候，需要重写这个⽅法，⽅便调试
```
# native ⽅法 
本地⽅法，具体是⽤C（C++）在DLL中实现的，然后通过JNI调⽤
# 什么是JNI: 
Java平台和本地C（C++）代码进⾏互操作的API，称为Java Native Interface (Java本地接⼝)