---
title:   新版JDK try-with-resource处理IO异常
date: 2021/09/25 21:12:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 变化点
1. JDK7之后的写法，JDK9⼜进⾏了改良，但是变化不⼤，记住下⾯的写法即可
2. 需要关闭的资源只要实现了java.lang.AutoCloseable，就可以⾃动被关闭
3. try()⾥⾯可以定义多个资源，它们的关闭顺序是最后在try()定义的资源先关闭。

```java
public static void test4() {
 try (FileInputStream fis = new FileInputStream("xdclass.txt");
 BufferedInputStream bis = new BufferedInputStream(fis);
 FileOutputStream fos = new FileOutputStream("copy.txt");
 BufferedOutputStream bos = new BufferedOutputStream(fos);
 ) {
 int size;
 byte[] buf = new byte[1024];
 while ((size = bis.read(buf)) != -1) {
 bos.write(buf, 0, size);
 }
 } catch (Exception e) {
 e.printStackTrace();
 }
 }
 ```