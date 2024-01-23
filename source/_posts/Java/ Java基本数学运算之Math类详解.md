---
title: Java基本数学运算之Math类详解
date: 2021/09/29 21:12:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 什么是Math类
1. Java操作数学运算相关的类
2. 构造函数被私有化，所以不允许创建对象
3. 都是静态⽅法，使⽤是直接类名.⽅法名

# 常⽤API⽅法讲解
```java
//计算平⽅根
 System.out.println(Math.sqrt(16));
 //计算⽴⽅根
 System.out.println(Math.cbrt(8));
 //两个数的最⼤，⽀持int, long, float,double
 System.out.println(Math.max(2.9,4.5));
 System.out.println(Math.min(2.9,4.5));
 //ceil向上取整，更⼤的值⽅向靠拢, 中⽂是天花板
 System.out.println(Math.ceil(19.7));
 System.out.println(Math.ceil(-20.1));
 //floor向下取整，更⼩的值⽅向靠拢，中⽂是地板意思
 System.out.println(Math.floor(19.7));
 System.out.println(Math.floor(-20.1));
 //随机数
 System.out.println(Math.random()); //⼩于1⼤于0的double类型的数
 //产⽣1到10的随机数，int⽅法进⾏转换它会去掉⼩数掉后⾯的数字即只获取整数部分,不是四舍
五⼊
 int random=(int)(Math.random()*10+1);
 ```
 # 产⽣随机数
 math.ramdom() ⼤于等于0，⼩于1