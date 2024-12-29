---
title:  java核⼼关键词this的⽤法和指向
date: 2021/09/4 20:08:00
tags:
  - Tag
categories:
  - Java
---

# this关键字
1. 当⼀个对象创建后，JVM会给这个对象分配⼀个引⽤⾃身的指针，这个指针的名字就是 this
2. 只能⽤于⾮静态⽅法体内，静态⽅法和代码块不能出现this
3. this就是指向当前对象本身

# 使⽤场景
1. this(参数类型1 参数名，...) 表示当前类对应的构造函数
2. ⽅法形参和对象的属性重名，⽤this来区分

```java
public void setAge(int age){
 this.age = age;
}
```