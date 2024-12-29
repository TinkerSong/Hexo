---
title:  Java进阶核⼼之集合框架Map介绍上集
date: 2021/09/9 22:54:00
tags:
  - Tag
categories:
  - Java
---
# 常⻅Map API语法
```java
Map<String,String> map = new HashMap<>();
//往map⾥⾯放key - value;
map.put("⼩明","⼴东⼴州");
map.put("⼩东","⼴东深圳");
//根据key获取value
map.get("⼩东");
//判断是否包含某个key
map.containsKey("⼩明");
//返回map的元素数量
map.size();
//清空容器
map.clear();
//获取所有value集合
map.values();
//返回所有key的集合
map.keySet()
//返回⼀个Set集合，集合的类型为Map.Entry , 是Map声明的⼀个内部接⼝，接⼝为泛型，定
义为Entry<K,V>，
//它表示Map中的⼀个实体(⼀个key-value对),主要有getKey(),getValue⽅法
Set<Map.Entry<String,String>> entrySet = map.entrySet();
//判断map是否为空
map.isEmpty();
```

# Map⾯试题
1. HashMap和TreeMap应该怎么选择
HashMap可实现快速存储和检索，但缺点是包含的元素是⽆序的，适⽤于在Map中插⼊、删除和定位元素.
TreeMap能便捷的实现对其内部元素的各种排序，但其⼀般性能⽐HashMap差,适⽤于按⾃然顺序或⾃定义顺序遍历键(key)
2. jdk1.7和jdk1.8中HashMap的主要区别
底层实现由之前的 “数组+链表” 改为 “数组+链表+红⿊树”
3. 什么时候开始转变
当链表节点较少时仍然是以链表存在，当链表节点较多时，默认是⼤于8时会转为红⿊树