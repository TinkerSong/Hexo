---
title: Java核⼼基础之If else条件语句
date: 2021/09/2 20:24:00
tags:
  - Tag
categories:
  - Java
---

# if 语句的使⽤
```java
//如果布尔表达式为true，则执⾏花括号⾥⾯的内容，如果语句体只有⼀句，则花括号可以不
写，但是推荐写
if(布尔表达式){
 //语句体
}
```
# if else 语句的使⽤，如果if条件为false，则else⾥⾯的内容会被执⾏
```java
if(布尔表达式){
 //语句体
}else{
 //语句体
}
```
# if else if else 语句的使⽤，⽤于判断多个条件
```java
if(布尔表达式1){
 //语句体
}else if(布尔表达式2){
 //语句体
}else if(布尔表达式3){
 //语句体
}else if(布尔表达式4){
 //语句体
}else{
 //语句体
}
```
:::info
if 语句⾄多有 1 个 else 语句，可以0个else，且else 语句在最后，类似前⾯的都不成
功，最后⼀定执⾏
if 语句可以有多个 else if 语句，它们必须在 else 语句之前
如果其中⼀个 else if 语句为 true，其他的 else if 以及 else 语句都将跳过执⾏
:::

# if else 嵌套
```java
int age = 30;
if(age > 10){
 if(age > 18){
 if(age>25){

 }else{

 }
 }else{

 }
}else{

}
```
