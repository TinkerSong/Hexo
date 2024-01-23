---
title: java进阶基础之Try Catch异常捕获
date: 2021/09/6 22:24:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 异常处理之捕获
1. 语法
```java
try{
 // 可能发⽣异常的代码
}catch(AExceptionName e){
 //出异常的时候处理
}catch(BExceptionName e){
}fianall{

}
```
2. try后⾯跟⼀个或多个catch块，或⼀个finally块，或两者的组合
3. catch 不能独⽴于 try ⽽单独存在
4. 如果代码没有对应的异常类进⾏捕获，则默认打印异常堆栈