---
title: java核⼼基础知识之修饰符 
date: 2021/08/17 20:34:00
tags:
  - Tag
categories:
  - Java
---

# 讲解java修饰符和使⽤场景
## 修饰符的作⽤是啥？⽤来定义类、⽅法或者变量的访问权限
## 两⼤类
    访问修饰符：
        限定类、属性或⽅法是否可以被程序⾥的其他部分访问和调⽤的修饰符
        private < default < protected < public
    ⾮访问修饰符：⽤来修饰或者辅助功能，
        例如static、final、abstract、synchronized等
## 主要记住：
    外部类修饰符： public或者为默认
    ⽅法、属性修饰符：private、default、protected、public
        public - 公开对外部可⻅
        protected - 对包和所有⼦类可⻅
        private - 仅对类内部可⻅
## ⽅法级别
|修饰符|当前类|同⼀包内|不同包中的⼦类|⼦类(不同包)|
|  :----: | :----:  | :----:| :----: | :----: |
|public|Y|Y|Y|Y|
|protected|Y|Y|Y|N|
|default|Y|Y|N|N|
|private|Y|N|N|N|
## 属性或者成员变量，都⽤private修饰，不⽤其他的，这个是java开发的约束
## Java中public class与class的区别
在⼀个*.java的⽂件中，只能有⼀个public class的声明，有多个public则编译报错，其类名称必须与⽂件名称完全⼀致,但是允许有多个class的声明，
```java
public class A{
 public static void main(String [] args){
 System.out.println("A");
 }
};
class B{};
class C{};
```
只有public修饰的类，才能在包外部包可⻅；否则只是包内私有的类，类不能被其他包访问。