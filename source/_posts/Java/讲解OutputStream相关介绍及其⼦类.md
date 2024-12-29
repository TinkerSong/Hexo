---
title: 讲解OutputStream相关介绍及其⼦类
date: 2021/09/20 23:22:00
tags:
  - Tag
categories:
  - Java
---

# OutputStream是输出字节流的⽗类，它是⼀个抽象类
:::info
void write(int b)
讲解：将指定的字节写⼊输出流

void write(byte[] b)throws IOException
讲解：将b.length个字节的byte数组写⼊当前输出流

void flush() throws IOException
讲解：write是写到缓冲区中，可以认为是内存中,当缓冲区满时系统会⾃动将缓冲区的内容写⼊
⽂件，但是⼀般还有⼀部分有可能会留在内存这个缓冲区中, 所以需要调⽤flush空缓冲区数据。

void close() throws IOException
讲解：关闭输⼊流并释放与该流关联的系统资源
:::

# 常⻅⼦类
FileOutputStream
1. 抽象类OutputStream⽤来具体实现类的创建对象, ⽂件字节输出流, 对⽂件数据以字节的形式进⾏输出的操作
2. 构造函数
```java
//传⼊输出的⽂件地址
public FileOutputStream(String name)
//传⼊⽬标输出的⽂件对象
public FileOutputStream(File file)
//传⼊⽬标输出的⽂件对象, 是否可以追加内容
public FileOutputStream(File file, boolean append)
```
3. 实战
```java
public static void main(String[] args) throws IOException {
 String dir = "C:\\Users\\79466\\Desktop;
 String name = "a.txt";
 String target = "b.txt";
 File file = new File(dir, name);
 InputStream inputStream = new FileInputStream(file);
 //会⾃动创建⽂件，但是不会创建多级⽬录下的⽂件
 OutputStream outputStream = new
FileOutputStream("/Users/xdclass/Desktop/test/"+target);
 // 不覆盖⽂件，追加数据
 //OutputStream outputStream = new
FileOutputStream("/Users/xdclass/Desktop/test/"+target,true);
 //testOutBuf(inputStream ,outputStream);
 testOut(inputStream,outputStream);
 }
 //单个字节读取，中⽂会有问题
 public static void testOut(InputStream inputStream, OutputStream
outputStream) throws IOException {
 int value =0 ;
 while ( value !=-1) {
 value = inputStream.read();
 outputStream.write(value);
 }
 //最后记得关闭流
 inputStream.close();
 outputStream.close();
 }
 public static void testOutBuf(InputStream inputStream, OutputStream
outputStream) throws IOException {
 byte[] buf = new byte[1024];
 int length;
 while ((length = inputStream.read(buf)) != -1) {
 outputStream.write(buf,0,length);
 }
 //最后记得关闭流
 inputStream.close();
 outputStream.close();
 }
```
ByteArrayOutputStream
ObjectOutputStream