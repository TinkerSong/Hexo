---
title:  字符流和字节流的桥梁OutputStreamWriter
date: 2021/09/24 21:34:00
tags:
  - Tag
categories:
  - Java
---

# OutputStreamWriter(继承writer)
1. 简介：
将字符流转换为字节流(看源码解释), 字符流通向字节流的桥梁,如果不指定字符集编码，则编码过程将使⽤平台默认的字符编码，如：GBK
2. 构造函数
```java
//使⽤系统默认编码集
public OutputStreamWriter(OutputStream out)
//指定指定编码集创建对象
public OutputStreamWriter(OutputStream out, String charsetName)
```
3. 常⽤API
```java
void write(int c)
讲解：写⼊⼀个字符

void write(char[] cbuf, int off, int len)
讲解：写⼊字符数组的⼀部分，通过off和len控制。

void write(String s, int off, int len)
讲解：写⼊字符数组的⼀部分，通过off和len控制。

void newLine()
讲解：写如⼀个换⾏符合

void close()
讲解：关闭输⼊流并释放与该流关联的系统资源

void flush()
讲解：write是写到缓冲区中，可以认为是内存中,当缓冲区满时系统会⾃动将缓冲区的内容写⼊⽂件，但是⼀般还有⼀部分有可能会留在内存这个缓冲区中, 所以需要调⽤flush空缓冲区数据。
```

4. 实战（指定编码写⼊，如果⽤其他编码打开则乱码，读取也是会乱码）
```java
public static void test2(String path) throws IOException {
 OutputStream out = new FileOutputStream(path);
 OutputStreamWriter osr = new OutputStreamWriter(out,"GBK");
 BufferedWriter bufw = new BufferedWriter(osr);
 String str = "欢迎来到⼩滴课堂xdclass.net";
 bufw.write(str);
 bufw.newLine();
 bufw.write("学习java课程");
 bufw.flush();
 bufw.close();
 }
 ```
 