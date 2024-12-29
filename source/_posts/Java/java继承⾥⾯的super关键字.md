---
title: java继承⾥⾯的super关键字
date: 2021/09/4 21:24:00
tags:
  - Tag
categories:
  - Java
---

# super关键字
1. ⼀个引⽤变量，⽤于引⽤⽗类对象
2. ⽗类和⼦类都具有相同的命名⽅法，要调⽤⽗类⽅法时使⽤
3. ⽗类和⼦类都具有相同的命名属性，要调⽤⽗类中的属性时使⽤
4. super也是⽗类的构造函数，格式 super(参数)
:::info
注意点 调⽤super() 必须是类构造函数中的第⼀条语句，否则编译不通过
:::

# 注意
1. 每个⼦类构造⽅法的第⼀条语句，都是隐含地调⽤super()，如果⽗类没有这种形式的构造函
数，那么在编译的时候就会报错
```java
public class Father {
 public Father(){
 System.out.println("father ⽆参构造函数");
 }
}
public class Children extends Father{
 public Children(){
 //默认存在，写和不写都⾏
 super();
 System.out.println("Child⽆参构造函数");
 }
}
```
2. this()和super()都指的是对象，均不可以在static环境中使⽤
包括：static变量,static⽅法，static语句块。

# 构造函数 super和this
1. this 和super在构造函数中只能有⼀个，且都必须是构造函数当中的第⼀⾏
2. 当⽗类的构造函数是⽆参构造函数时，在⼦类的构造函数中，不⽤显式super()去调⽤⽗类的构造函数.
3. 当⽗类的构造函数是有参构造函数时，如果⼦类的构造函数中不写super()进⾏调⽤⽗类的构造函数，编译器会报错

# java继承后类的初始化顺序
问题：静态代码块、⾮静态代码、⽗类/⼦类⽆参构造⽅法、⽗类/⼦类的⼀般⽅法
```java
public class Father {
 static {
 System.out.println("⽗类静态代码块");
 }
 public Father(){
 System.out.println("father ⽆参构造函数");
 }
 public Father(int age){
 System.out.println("father 有参构造函数");
 }
 public void sleep(){
 System.out.println("father sleep⽅法");
 }
}
public class Children extends Father{
 static {
 System.out.println("Child静态代码块");
 }
 public Children(){
 //super();
 System.out.println("Child⽆参构造函数");
 super.sleep();
 }
 public void sleep(){
 System.out.println("Child sleep⽅法");
 }
}
```