---
title: Java集合⼯具类Collections讲解上集
date: 2021/09/14 20:14:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# Collections⼯具类
Java⾥关于集合的⼯具类，包含有各种有关集合操作的静态多态⽅法，不能实例化(把构造函数私有化)
```java
public class Collections {
 // Suppresses default constructor, ensuring noninstantiability.
 private Collections() {
 }
 ```

# 和Collection的区别
1. Collection是接⼝，提供了对集合对象进⾏基本操作的通⽤接⼝⽅法，List、Set等多种具体的实现类
2. Collections是⼯具类，专⻔操作Collection接⼝实现类⾥⾯的元素

# 常⻅⽅法
1. 排序 sort(List list)
按⾃然排序的升序排序
```java
List<String> list = new ArrayList<>();
 list.add("aaaa");
 list.add("zzz");
 list.add("gggg");
 System.out.println(list);
 Collections.sort(list);
 System.out.println(list);
 ```
 sort(List list, Comparator c) ⾃定义排序规则，由Comparator控制排序逻辑
 ```java
 List<String> list = new ArrayList<>();
 list.add("aaaa");
 list.add("zzz");
 list.add("gggg");
 System.out.println(list);
 //默认升序
 Collections.sort(list, Comparator.naturalOrder());
 System.out.println(list);
 //降序
 Collections.sort(list, Comparator.reverseOrder());
 System.out.println(list);
 ```

 2. 随机排序 shuffle(List list)
 ```java
 List<String> list = new ArrayList<>();
 list.add("1");
 list.add("2");
 list.add("3");
 list.add("4");
 list.add("5");
 list.add("6");
 list.add("7");
 list.add("8");
 list.add("9");
 list.add("10");
 list.add("J");
 list.add("Q");
 list.add("K");
 System.out.println(list);
 Collections.shuffle(list);
 System.out.println(list);
 ``` 