---
title: java异常处理之throws throw关键词
date: 2021/09/7 23:24:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 代码出异常常⻅的处理⽅法
1. try catch捕获
2. throws 声明异常 往外抛出
语法：throws⼦句放在⽅法参数列表的右括号之后，⼀个⽅法可以声明抛出多个异常，多个异常之间⽤逗号隔开。
例⼦
```java
public class Main {
 public static void readChar() throws
IOException,RemoteException {
 int input = System.in.read();
 }
}
```
# try catch中捕获了异常，处理⽅法
1. 当前捕获⾃⼰处理
2. 捕获⾃⼰处理然后继续往外⾯抛异常
语法
```java
throw new ExceptionName("异常信息");
```
例⼦
```java
throw new IOException("File not found");
```
:::info
总结：当抛出⼀个被检查的异常，我们必须使⽤try-catch块来处理它，或者在⽅法声明中使⽤throws⼦句继续往外抛
:::