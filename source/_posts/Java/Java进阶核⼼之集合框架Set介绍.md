---
title: Java进阶核⼼之集合框架Set介绍
date: 2021/09/10 20:14:00
tags:
  - Tag
categories:
  - Java
---

# 什么是Set数据结构
1. Set相对于List是简单的⼀种集合,具有和 Collection 完全⼀样的接⼝，只是实现上不同，Set不保存重复的元素，存储⼀组唯⼀，⽆序的对象。
2. Set中的元素是不能重复的, 实现细节可以参考Map，因为这些Set的实现都是对应的Map的⼀种封装。⽐如HashSet是对HashMap的封装，TreeSet对应TreeMap
3. Set底层是⼀个HashMap，由于HashMap的put()⽅法是⼀个键值对，当新放⼊HashMap的Entry中key 与集合中原有Entry的key相同（hashCode()返回值相等，通过equals⽐较也返回true），新添加的Entry的value会将覆盖原来Entry的value，但key不会有任何改变。
4. 允许包含值为null的元素，但最多只能有⼀个null元素。

# 常⻅的实现类
1. HashSet
HashSet类按照哈希算法来存取集合中的对象，存取速度⽐较快
对应的Map是HashMap，是基于Hash的快速元素插⼊，元素⽆顺序。
2. TreeSet
TreeSet类实现了SortedSet接⼝，能够对集合中的对象进⾏排序
```java
//创建对象,HashSet和TreeSet api⼀样
Set<Integer> set = new HashSet<>();
//往容器⾥⾯添加对象
set.add("jack");
//清空元素
set.clear();
//返回⼤⼩
set.size();
//根据对象删除元素
set.remove("jack");
//是否为空
set.isEmpty();
```
# 两者常⻅区别
1. HashSet不能保证元素的排列顺序，TreeSet是SortedSet接⼝的唯⼀实现类，可以确保集合元素处于排序状态
2. HashSet底层⽤的是哈希表，TreeSet采⽤的数据结构是红⿊树（红⿊树是⼀种特定类型的⼆叉树）
3. HashSet中元素可以是null，但只能有⼀个，TreeSet不允许放⼊null
4. ⼀般使⽤HashSet，如果需要排序的功能时，才使⽤TreeSet（性能原因）