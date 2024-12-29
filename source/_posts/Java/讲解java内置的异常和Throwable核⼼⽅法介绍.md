---
title: 讲解java内置的异常和Throwable核⼼⽅法介绍
date: 2021/09/6 21:24:00
tags:
  - Tag
categories:
  - Java
---

# java内置异常
1. 可查异常（必须要在⽅法⾥⾯捕获或者抛出）
ClassNoFoundException 应⽤程序试图加载类，找不到对应的类
IllegalAccessException 拒绝访问⼀个类的时候
NoSuchFieldExcetion 请求的变量不存在
NoSuchMethodException ⽅法不存在
2. 不可查异常
ArrayIndexOutOfBoundsException 数组索引越界
ClassCastException 强制失败抛出异常
NullPointerException 需要对象的地⽅使⽤ null 时，抛出该异常
NumberFormatException 将字符串转换成⼀种数值类型，但该字符串不能转换为适当
格式时，抛出该异常
# Throwable类核⼼⽅法
1. public String getMessage()
异常的详细信息
2. public Throwable getCause()
异常原因
3. public void printStackTrace()
打印错误的堆栈信息，即错误输出流，可以看到错误原因和所在位置
4. public StackTraceElement [] getStackTrace()
堆栈层次的数组，下标为0的元素代表栈顶，最后⼀个元素代表⽅法调⽤堆栈的栈底