---
title: Java⾯向对象编程之抽象
date: 2021/09/5 22:24:00
tags:
  - Tag
categories:
  - Java
---

# 什么是抽象
1. 需求
动物都有年龄和名称，但是吃的不⼀样，⽺吃草，⽼⻁吃⾁，但是都是闭着眼睛睡觉的
⻋，都有名称和价格，也有跑的⽅法，但是最⾼速度或者动⼒来源不⼀样
2. 当⽗类的某些⽅法不确定时，可以⽤abstract关键字来修饰该⽅法，即抽象⽅法，⽤abstract来修饰该类，即抽象类
3. 抽象类将事物的共性的东⻄提取出来，由⼦类继承去实现，代码易扩展、易维护
4. java中的抽象类和抽象⽅法
```java
//抽象类
abstract class 类名{
}
//抽象⽅法，不能有⽅法主体
abstract 返回类型 ⽅法名();
```
```java
public abstract class Vehicle {

 public abstract void run();
 public void stop(){
 System.out.println("停在路上");
 }
}
class Bicycle extends Vehicle{
 @Override
 public void run() {
 System.out.println("⼈⼯驱动");
 }
}
class Automobile extends Vehicle{
 @Override
 public void run() {
 System.out.println("汽油驱动");
 }
}
```
# 抽象特点：
1. 抽象类的特点
:::info
抽象类不能被实例化，因为抽象类中⽅法未具体化，这是⼀种不完整的类，所以不能直
接实例化，编译⽆法通过
抽象类中不⼀定包含抽象⽅法，但是有抽象⽅法的类必定是抽象类
如果⼀个抽象类中可以没有抽象⽅法，这样做的⽬的是为了此类不能被实例化。
抽象类的⼦类必须给出抽象类中的抽象⽅法的具体实现，否则⼦类也是抽象类，需要⽤abstract声明
抽象类不能使⽤final关键字修饰，因为final修饰的类是⽆法被继承
:::
2. 抽象⽅法的特点
:::info
抽象类中的抽象⽅法只是声明，不包含⽅法体
抽象⽅法不能⽤private修饰，因为抽象⽅法必须被⼦类实现（覆写），⽽private权限
对于⼦类来 说是不能访问的
⼀个类继承了⼀个抽象类，那么它必须全部覆写抽象类中的抽象⽅法，当然也可以不全部覆写，如果 不覆写全部抽象⽅法则这个⼦类也必须是抽象类
:::
3. 构造⽅法，类⽅法（即static 修饰的⽅法）不能声明为抽象⽅法
