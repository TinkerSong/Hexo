---
title: Buffered Reader字符输⼊缓冲流实战
date: 2021/09/22 21:22:00
tags:
  - Tag
categories:
  - Java
---

# 目的
1. 为了提⾼了单个字符读写的效率，进⾏字符批量的读写; 为了提⾼字符流读写的效率，引⼊了缓冲机制
2. 采⽤包装设计模式（锦上添花）
3. BufferedReader
简介：当BufferedReader在读取⽂本⽂件时，会先尽量从⽂件中读⼊字符数据并放满缓冲区，⽽之后若使⽤read()⽅法，会先从缓冲区中进⾏读取。如果缓冲区数据不⾜，才会再从⽂件中读取

# 构造函数
```java
BufferedReader(Reader in)
BufferedReader(Reader in, int sz)
讲解：创建⼀个使⽤指定⼤⼩输⼊缓冲区的缓冲字符输⼊流。
```

# 常⽤API
```java
 boolean ready()
 讲解：判断此流是否已准备好被读取，依赖其他流，所以⼀般需要做判断

 int read()
 讲解：读取单个字符

 int read(char[] cbuf, int off, int len)
 讲解：读取⼀部分字符到数组⾥⾯，从数组下标off处放置length⻓度的字符

 String readLine()
 讲解:读取⼀整⾏⽂本⾏，返回⼀整⾏字符串，如果读到⾏尾了就返回null,注意返回的⼀⾏字符中不包含换⾏符

 void close()
 讲解：关闭流释放资源
 ```
 # 实战
 ```java
 public static void test1(String path) throws IOException {
 BufferedReader reader = new BufferedReader(new FileReader(path));
 if (!reader.ready()) {
 System.out.println("⽂件流暂时⽆法读取");
 return;
 }
 int size ;
 char[] cbuf = new char[1024];
 while ((size = reader.read(cbuf, 0, cbuf.length)) != -1) {
 System.out.println(new String(cbuf, 0, size));
 }
 reader.close();
 }
 ```