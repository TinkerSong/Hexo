---
title: Java异常进阶之Finally讲解和多重捕获
date: 2021/09/6 23:24:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# ⼀个 try 代码块后⾯跟多个 catch 代码块的情况就叫多重捕获
1. 语法
```java
try{
 // 可能发⽣异常的代码
}catch(ExceptionName1 e1){
 //出异常的时候处理
}catch(ExceptionName2 e2){
 //出异常的时候处理
}
```
2. 代码中发⽣异常，异常被抛给第⼀个 catch 块, 如果不匹配则继续往下⼀个catch进⾏传递

# finally关键字
1. ⽤来创建在 try 代码块后⾯执⾏的代码块
2. finally 代码块中的代码总会被执⾏
3. ⼀般⽤于资源回收释放等操作
4. 语法：
```java
try{
 // 可能发⽣异常的代码
}catch(ExceptionName1 e1){
 //出异常的时候处理
}finally{
 //肯定执⾏的代码
}
```
或者
```java
try{
 // 可能发⽣异常的代码
}finally{
 //肯定执⾏的代码
}
```
# 尽量不要在finally⾥⾯使⽤return，会忽略try catch⾥⾯的return，容易造成未知的bug
```java
public static int divide(int num1, int num2){
 try {
 int result = num1/num2;
 return result;
 }catch (Exception e){
 System.out.println("出异常");
 }finally {
 System.out.println("finally执⾏了");
 return -2;
 }
 // return -1;
 }
 ```

 # 三者的组合
 try，catch和finally块有两种可能的组合:try-catch-finally或try-finally。