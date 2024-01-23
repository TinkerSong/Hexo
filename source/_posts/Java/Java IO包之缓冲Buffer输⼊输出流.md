---
title: Java IO包之缓冲Buffer输⼊输出流
date: 2021/09/21 20:22:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 什么是缓冲 Buffer 
它是内存空间的⼀部分，在内存空间中预留了⼀定的存储空间，这些存储空间⽤来缓冲输⼊或输出的数据，这部分空间就叫做缓冲区，缓冲区是具有⼀定⼤⼩的，

# 为什么要⽤缓冲
1. 缓冲，缓和冲击，例如操作磁盘⽐内存慢的很多，所以不⽤缓冲区效率很低。
2. 数据传输速度和数据处理的速度存在不平衡，⽐如你每秒要写100次硬盘，对系统冲击很⼤，浪费了⼤量时间在忙着处理开始写和结束写这两个事件，⽤buffer暂存来，变成每10秒写⼀次硬盘，数据可以直接送往缓冲区，⾼速设备不⽤再等待低速设备，对系统的冲击就很⼩，写⼊效率⾼了。

# Java IO包⾥⾯的两个缓冲类（⾼级流）
1. BufferInputStream 和 BufferOutputStream
2. 采⽤包装设计模式（锦上添花的意思）
3. 画图

# BufferInputStream 缓冲字节输⼊流
1. BufferedInputStream 通过预先读⼊⼀整段原始输⼊流数据⾄缓冲区中，⽽外界对BufferedInputStream的读取操作实际上是在缓冲区上进⾏，如果读取的数据超过了缓冲区的范围，那么BufferedInputStream负责重新从原始输⼊流中载⼊下⼀截数据填充缓冲区，然后外界继续通过缓冲区进⾏数据读取。
2. 好处：避免了⼤量的磁盘IO，原始的InputStream类实现的read是即时读取的，每⼀次读取都会是⼀次磁盘IO操作（哪怕只读取了1个字节的数据），如果数据量巨⼤，这样的磁盘消耗⾮常可怕。
3. 缓冲区的实现: 读取可以读取缓冲区中的内容，当读取超过缓冲区的内容后再进⾏⼀次磁盘IO，载⼊⼀段数据填充缓冲，下⼀次读取⼀般情况就直接可以从缓冲区读取，减少了磁盘IO。
4. 默认缓冲区⼤⼩是8k, int DEFAULT_BUFFER_SIZE = 8192;
5. 常⻅构造函数
```java
//对输⼊流进⾏包装，⾥⾯默认的缓冲区是8k
public BufferedInputStream(InputStream in);
//对输⼊流进⾏包装,指定创建具有指定缓冲区⼤⼩的
public BufferedInputStream(InputStream in,int size);
```
# 常⽤的两个⽅法
```java
/从输⼊流中读取⼀个字节
public int read();
//从字节输⼊流中给定偏移量处开始将各字节读取到指定的 byte 数组中。
public int read(byte[] buf,int off,int len);
//关闭释放资源，关闭的时候这个流即可，InputStream会在⾥⾯被关闭
void close();
```
# BufferOutputStream 缓冲字节输出流
常⻅构造函数
```java
//对输出流进⾏包装,⾥⾯默认的缓冲区是8k
public BufferedOutputStream(OutputStream out);
//对输出流进⾏包装,指定创建具有指定缓冲区⼤⼩的
public BufferedOutputStream(OutputStream out,int size);
```

# 常⽤的三个⽅法
```java
//向输出流中输出⼀个字节
 public void write(int b);
 //将指定 byte 数组中从偏移量 off 开始的 len 个字节写⼊缓冲的输出流。
 public void write(byte[] buf,int off,int len);
 //刷新此缓冲的输出流，强制使所有缓冲的输出字节被写出到底层输出流中。
 public void flush();
 //关闭释放资源，关闭的时候这个流即可，OutputStream会在⾥⾯被关闭, JDK7新特性try(在这
⾥声明的会⾃动关闭){}
 void close();
```