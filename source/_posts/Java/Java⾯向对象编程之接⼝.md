---
title: Java⾯向对象编程之接口
date: 2021/09/5 21:24:00
tags:
  - Tag
categories:
  - Java
---

# 什么是接⼝
1. 是抽象⽅法的集合，接⼝通常以interface来声明，⼀个类通过继承接⼝的⽅式，从⽽来继承接⼝的抽象⽅法
2. 语法
```java
interface 名称 [extends 其他的接⼝名] {
 // 声明变量
 // 抽象⽅法
 int getMoney();
}
```
* 接⼝的特点
 * 接⼝的⽅法都是抽象⽅法，默认都是 public abstract，其他修饰符都会报错
 * 接⼝中可以含有变量，但是接⼝中的变量会被隐式的指定为 **public static final**
 * 类描述对象的属性和⽅法，⽽接⼝则包含类要实现的⽅法
 * 接⼝⽆法被实例化，需要被实现才⾏
 * ⼀个实现接⼝的类，必须实现接⼝内所描述的所有⽅法，否则就必须声明为抽象类
* 接⼝和类的区别
* 接⼝没有构造函数
 * 接⼝⾥可以有静态⽅法和⽅法体
 * 接⼝中所有的⽅法必须是抽象⽅法（JDK8之后就不是）
 * 接⼝不是被类继承了，⽽是要被类实现
 * 接⼝⽀持多继承, 类不⽀持多个类继承
* 接⼝的实现implements
 * 当类实现接⼝的时候，类要实现接⼝中所有的⽅法，不然类必须声明为抽象的类，使⽤implements关键字实现所有接⼝
 * 语法
:::info

```java
class 类名 implements 接⼝名称[, 其他接⼝名称, 其他接⼝名称]{
 //要实现的⽅法
}
```

# 注意
⼀个类只能继承⼀个类，但是能实现多个接⼝
接⼝能继承另⼀个接⼝，接⼝的继承使⽤extends关键字，和类继承⼀样

# JDK8新特性
1. interface中可以有static⽅法，但必须有⽅法实现体，该⽅法只属于该接⼝，接⼝名直接调⽤该⽅法
2. 接⼝中新增default关键字修饰的⽅法，default⽅法只能定义在接⼝中，可以在⼦类或⼦接⼝中被重写
3. default定义的⽅法必须有⽅法体
4. ⽗接⼝的default⽅法如果在⼦接⼝或⼦类被重写，那么⼦接⼝实现对象、⼦类对象，调⽤该⽅法，以重写为准
5. 本类、接⼝如果没有重写⽗类（即接⼝）的default⽅法，则在调⽤default⽅法时，使⽤⽗类定义的default⽅法逻辑

```java
public interface IPay{
 // static修饰符定义静态⽅法
 static void staticMethod() {
 System.out.println("接⼝中的静态⽅法");
 }

 // default修饰符定义默认⽅法 ,默认⽅法不是抽象⽅法，可以不重写也可以重写
 default void defaultMethod() {
 System.out.println("接⼝中的默认⽅法");
 }
} 
```
```java
// static⽅法必须通过接⼝类调⽤
 IPay.staticMethod();

 //default⽅法必须通过实现类的对象调⽤
 new IPay().defaultMethod();
```