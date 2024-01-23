---
title: JavaIO流内部异常处理
date: 2021/09/25 20:12:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 完成⼀个⽂件的拷⻉
1. 写法⼀(以前内容)
```java
try {
 FileInputStream fis = new FileInputStream("xdclass.txt");
 BufferedInputStream bis = new BufferedInputStream(fis);
 FileOutputStream fos = new FileOutputStream("copy.txt");
 BufferedOutputStream bos = new BufferedOutputStream(fos);
 int size;
 byte[] buf = new byte[1024];
 while ((size = bis.read(buf)) != -1) {
 bos.write(buf, 0, size);
 }
 //刷新此缓冲的输出流，才可以保证数据全部输出完成,close会⾃动关闭
 //bos.flush();
 //关闭的时候只需要关闭最外层的流就⾏了，源码⾥⾯会⾃动关闭inputstream对象的
 bis.close();
 bos.close();
 } catch (Exception e) {
 e.printStackTrace();
 }
 ```
 2. 写法⼆(JDK6之前，⼤部分⼈还停留这个写法)
 ```java
 BufferedInputStream bis = null;
 BufferedOutputStream bos = null;
 try {
 FileInputStream fis = new FileInputStream("xdclass.txt");
 bis = new BufferedInputStream(fis);
 FileOutputStream fos = new FileOutputStream("copy.txt");
 bos = new BufferedOutputStream(fos);
 int size;
 byte[] buf = new byte[1024];
 while ((size = bis.read(buf)) != -1) {
 bos.write(buf, 0, size);
 }
 } catch (Exception e) {
 e.printStackTrace();
 } finally {
 if (bis != null) {
 try {
 bis.close();
 } catch (IOException e) {
 e.printStackTrace();
 } finally {
 if (bos != null) {
 try {
 bos.close();
 } catch (IOException e) {
 e.printStackTrace();
 }
 }
 }
 }
 }
 ```
