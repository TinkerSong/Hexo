---
title: Java⾯向对象编程之InstanceOf关键词和多态
date: 2021/09/5 23:24:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# InstanceOf 关键词
1. 是Java的⼀个⼆元操作符（运算符）,也是Java的保留关键字
2. 作⽤
判断⼀个类是否实现了某个接⼝，或者判断⼀个实例对象是否属于⼀个类
语法
```java
//如果该object 是该class的⼀个实例，那么返回true。如果该object 不是该class的
⼀个实例，或者object是null，则返回false
boolean result = object instanceof class
参数：
　　result ：boolean类型。
　　object ：必选项。任意对象表达式。
　　class：必选项。任意已定义的对象类。
```
对象类型强制转换前的判断
```java
Person p1 = new Student();
//判断对象p是否为Student类的实例
if(1p instanceof Student)
{
 //向下转型
 Student s = (Student)p1;
}
```
# ⽅法重写和重载
1. ⽅法重写 overriede
⼦类对⽗类的允许访问的⽅法的实现过程进⾏重新编写,
注意点
返回值和形参都不能改变
⽗类的成员⽅法只能被它的⼦类重写
final 和 static的⽅法不能被重写
构造⽅法不能被重写
访问权限不能⽐⽗类中被重写的⽅法的访问权限更低
2. ⽅法重载 overload
⼀个类⾥⾯，⽅法名字相同但参数不同，返回类型可以相同也可以不同
⽐如构造函数重载

# 注意核⼼区分
1. override是在不同类之间的⾏为，overload是在同⼀个类中的⾏为
2. 总结：Java多态
同⼀个⾏为具有多个不同表现形式或形态的能⼒

常⻅的⽅式
:::info
继承⽅法重写
同类⽅法重载
抽象⽅法
接⼝
:::