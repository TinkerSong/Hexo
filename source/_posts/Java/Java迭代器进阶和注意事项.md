---
title: Java迭代器进阶和注意事项
date: 2021/09/10 22:14:00
tags:
  - Tag
categories:
  - Java
---

# 迭代器是⼀种设计模式

# 三个核⼼⽅法
:::info
- boolean hashNext()
 - ⽤于判断iterator内是否有下个元素，如果有则返回true，没有则false
- Obejct next()
 - 返回iterator的下⼀个元素，同时指针也会向后移动1位
- void remove()
 - 删除指针的上⼀个元素
 - 只有当next执⾏完后，才能调⽤remove函数
 - 如要删除第⼀个元素，不能直接调⽤ remove(),要先next⼀下()否则调⽤remove⽅法是
会抛出异常的
:::

# 注意
迭代器遍历元素时不能通过Collection接⼝中的remove⽅法删除元素，只能⽤Iterator的remove⽅法删除元素; 原因 某个线程在 Collection 上进⾏迭代时，不允许另⼀个线程修改该 Collection
```java
public static void testList(){
 List<String> list = new ArrayList<>();
 list.add("jack");
 list.add("tom");
 list.add("mary");
 list.add("tim");
 list.add("tony");
 list.add("eric");
 list.add("jack");
 Iterator<String> iterator = list.iterator();
 while (iterator.hasNext()){
 String str = iterator.next();
 if("jack".equals(str)){
 list.remove(str);//ConcurrentModificationException并发修改异常
 }
 System.out.println(str);
 }
 }
```

#     
# 和for循环对⽐
1. for循环适合顺序访问，或者通过下标进⾏访问的
2. 迭代器适合链式结构
3. 最终看使⽤场景，性能会有轻微差别，但是可以忽略