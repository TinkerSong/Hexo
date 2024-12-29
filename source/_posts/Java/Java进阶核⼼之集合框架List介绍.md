---
title: Java进阶核⼼之Collection集合框架概要
date: 2021/09/9 21:24:00
tags:
  - Tag
categories:
  - Java
---

# 什么是List数据结构
:::info 
List接⼝是⼀个有序的 Collection，线性列表接⼝，能够精确的控制每个元素插⼊的位置，能
够通过索引(类似于数组的下标)来访问List中的元素，第⼀个元素的索引为 0，⽽且允许有相同
的元素,接⼝存储⼀组不唯⼀，有序（插⼊顺序）的对象。
:::

# 常⻅的实现类
1. ArrayList
基于数组实现，是⼀个动态的数组队列，但它和Java中的数组⼜不⼀样，它的容量可以⾃动增⻓
可以存储任意多的对象，但是只能存储对象，不能存储原⽣数据类型例如int
2. LinkedList
基于的数据结构是链表，⼀个双向链表，链表数据结构的特点是每个元素分配的空间不必连续
插⼊和删除元素时速度⾮常快，但访问元素的速度较慢
3. 常⻅List API语法
```java
//创建对象,LinkedList和ArrayList api⼀样
List<String> list = new ArrayList<>();
//往容器⾥⾯添加对象
list.add("jack");
//根据索引获取元素
list.get(index);
//更新⼀个元素
list.set(index, “⼩滴课堂”);
//返回⼤⼩
list.size();
//根据索引删除⼀个元素
list.remove(index);
//根据对象删除元素
list.remove("jack");
//清空元素
list.clear();
//是否为空
list.isEmpty();
```
```java
//LinkedList特有api
//获取第⼀个元素
list.getFirst();
//获取最后⼀个元素
list.getLast();
```

# 两者常⻅区别 (经典⾯试题)
1. 两个都是List的接⼝，两个都是⾮线程安全的
2. ArrayList是基于动态数组的数据结构，⽽LinkedList是基于链表的数据结构
3. 对于随机访问get和set（查询操作），ArrayList要优于LinkedList，因为LinkedList要移动指针
4. 对于增删操作（add和remove），LinkedList优于ArrayList。