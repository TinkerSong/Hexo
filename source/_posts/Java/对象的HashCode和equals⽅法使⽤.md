---
title: 对象的HashCode和equals⽅法使⽤
date: 2021/09/18 22:14:00
tags:
  - Tag
categories:
  - Java
---

# HashCode⽅法
1. 顶级类Object⾥⾯的⽅法，所有类都是继承Object的，返回值int类型
2. 根据⼀定的hash规则(存储地址，字段，或者⻓度等)，映射成⼀个数值，即散列值

# Equals⽅法
1. 顶级类Object⾥⾯的⽅法，所有类都是继承Object的，返回值boolean类型
2. 根据⾃定义的匹配规则，⽤于匹配两个对象是否⼀样, ⼀般逻辑是如下
```java
//判断地址是否⼀样
//⾮空判断和class类型判断
//强转
//对象⾥⾯的字段⼀⼀匹配
```

# 重写规则
```java
 class User {
 private int age;
 private String name;
 private Date time;
 //省略setter和getter⽅法
 @Override
 public boolean equals(Object o) {
 if (this == o) return true;
 if (o == null || getClass() != o.getClass()) return false;
 Student student = (Student) o;
 return age == student.age &&
 Objects.equals(name, student.name) &&
 Objects.equals(time, student.time);
 }
 @Override
 public int hashCode() {
 return Objects.hash(age, name, time);
 }
}
```

# 问题：当向集合中插⼊对象时，如何判别在集合中是否已经存在该对象，⽐如Set确保存储对象的唯⼀，并判断是不是同个对象呢？
1. 依据hashCode和equals进⾏判断，所以Set存储的对象必须重写这两个⽅法判断两个对象是否⼀样，⾸先判断插⼊obj的hashcode值是否存在，hashcode值不存在则直
2 .接插⼊集合，值存在则还需判断equals⽅法判断对象是否相等