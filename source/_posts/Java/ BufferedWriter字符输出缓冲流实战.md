---
title:  BufferedWriter字符输出缓冲流实战
date: 2021/09/22 22:22:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# BufferedWriter
1. 简介：写⼊的数据并不会先输出到⽬的地，⽽是先存储⾄缓冲区中。如果缓冲区中的数据满了，才会⼀次对⽬的地进⾏写出
2. 构造函数
```java
BufferedWriter(Writer out)
BufferedWriter(Writer out, int sz)
```
3. 常⽤API
```java
void write(int c)
//讲解：写⼊⼀个字符

void write(char[] cbuf, int off, int len)
//讲解：写⼊字符数组的⼀部分，通过off和len控制。

void write(String s, int off, int len)
//讲解：写⼊字符数组的⼀部分，通过off和len控制。

void newLine()
//讲解：写如⼀个换⾏符合

void close()
//讲解：关闭输⼊流并释放与该流关联的系统资源

void flush()
//讲解：write是写到缓冲区中，可以认为是内存中,当缓冲区满时系统会⾃动将缓冲区的内容写⼊⽂件，但是⼀般还有⼀部分有可能会留在内存这个缓冲区中, 所以需要调⽤flush空缓冲区数据
```
4. 实战(会⾃动创建⽂件)
```java
public static void test1(String path) throws IOException {
 BufferedWriter writer = new BufferedWriter(new FileWriter(path));
 char ch = '⼩';
 //写⼊⼀个字符
 writer.write(ch);
 String other = "滴课堂xdclass.net";
 //写⼊⼀个字符数组
 writer.write(other.toCharArray(), 0, other.length());
 //写⼊换⾏符
 writer.newLine();
 String newLine = "学习java架构课程";
 //写⼊⼀个字符串。
 writer.write(newLine);
 writer.close();
 }
```