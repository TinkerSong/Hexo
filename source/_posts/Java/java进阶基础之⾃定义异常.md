---
title: java进阶基础之⾃定义异常
date: 2021/09/7 22:24:00
tags:
  - Tag
categories:
  - Java
---

# 为什么要使⽤⾃定义异常
当前JDK内置的异常不满⾜需求,项⽬会出现特有异常
⾃定义异常可以让业务更清晰
# 如何进⾏⾃定义异常
异常都是继承⾃Exception类，所以我们要⾃定义的异常也需要继承这个基类。
例⼦
```java
public class BaseException extends Exception {
    private String errorMessage;
 private String errorCode;
 public BaseException(String errorCode,String errorMessage){
 super(errorMessage);
 this.errorCode = errorCode;
 this.errorMessage = errorMessage;
 }
 public String getErrorMessage() {
 return errorMessage;
 }
 public String getErrorCode() {
 return errorCode;
 }
 public void setErrorCode(String errorCode) {
 this.errorCode = errorCode;
 }
 public void setErrorMessage(String errorMessage) {
 this.errorMessage = errorMessage;
 }
}
```
