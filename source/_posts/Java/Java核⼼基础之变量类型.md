---
title: Java核⼼基础之变量类型
date: 2021/08/30 20:34:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 讲解java类⾥⾯的变量类型
## 类变量(静态变量)：
使⽤static声明的变量，可以直接使⽤ 类名.变量名访问
⼀个类不管创建了多少个对象，类只拥有类变量的⼀份拷⻉，数值默认值是0，布尔型默认值是false，引⽤类型默认值是null
## ⽣命周期
在第⼀次被访问时创建，在程序结束时销毁
声明为public类型，⼀般这样声明 public static final
存储在⽅法区，和堆栈不⼀样的⼀个空间
```java
public class Student{
 public static final String PREFIX = "我是谁！";
}
```
## 实例变量(属性)
需要使⽤对象.变量名才可以访问
对象被实例化之后，实例变量的值就跟着确定，可以是赋值，也可以是默认值
⽣命周期
在对象创建的时候创建，在对象被销毁的时候销毁
访问修饰符可以修饰实例变量，⼀般是私有的，private修饰，然后通过⽅法来进⾏查看或者修改
```java
public class Student {
 //介绍前缀
 public static final String PREFIX = "我是叫";

 //年龄
 private int age;

 //姓名
 private String name;

 public int getAge() {
 return age;
 }
 public void setAge(int age) {
 this.age = age;
 }
 public String getName() {
 return name;
 }
 public void setName(String name) {
 this.name = name;
 }
}
```
# 局部变量
⽅法中的变量
声明在⽅法、构造⽅法、语句块、形式参数等
⽣命周期
当它们执⾏完成后，变量将会被销毁
访问修饰符不能⽤于局部变量
局部变量没有初始值，必须初始化后才可以被使⽤
```java
public class Student {
 //介绍前缀
 public static final String PREFIX = "我是谁";

 //年龄
 private int age;

 //姓名
 private String name;

 public int getAge() {
 return age;
 }
 public void setAge(int age) {
 this.age = age;
 }
 public String getName() {
 return name;
 }
 public void setName(String name) {
 this.name = name;
 }

 //⾃我介绍⽅法
 public String introduce(){
 String content = PREFIX + name + "，年龄是" + age;
 return content;
 }
}
```