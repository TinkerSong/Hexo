---
title: Java字符输出流Writer讲解
date: 2021/09/22 21:22:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# Writer是输出字符流的⽗类，它是⼀个抽象类
:::info
public void write(int c) throws IOException
讲解：直接将int型数据作为参数的话，是不会写⼊数字的，⽽是现将数字按照ascll码表转换为相应的字符，然后写⼊

public void write(String str) throws IOException
讲解：要想实现数字和中⽂的写⼊，必须要⽤String为参数的Write

public abstract void write(char cbuf[], int off, int len) throws
IOException;
讲解：将cbuf字符数组的⼀部分写⼊到流中，但能不能写len个字符取决于cbuf中是否有那么多

void flush() throws IOException
讲解：write是写到缓冲区中，可以认为是内存中,当缓冲区满时系统会⾃动将缓冲区的内容写⼊⽂件，但是⼀般还有⼀部分有可能会留在内存这个缓冲区中, 所以需要调⽤flush空缓冲区数据。对⽐BufferWriter需要实时查表，效率低，其实缓冲区IO的各个都有，只不过很⼩被忽
略,OutputStream都有flush⽅法，看⼦类是否有重写

void close() throws IOException
讲解：关闭输⼊流并释放与该流关联的系统资源
:::

# 常⻅⼦类
FileWriter ⽤来写出字符⽂件的实现类
:::info
public FileWriter(String fileName) throws IOException
 讲解：如果⽂件不存在，这会⾃动创建。如果⽂件存在，则会覆盖

 public FileWriter(File file) throws IOException
 讲解：如果⽂件不存在，这会⾃动创建。如果⽂件存在，则会覆盖

 public FileWriter(String fileName, boolean append) throws
IOException
 讲解：加⼊true参数，会实现对⽂件的续写，使⽤false则会实现对⽂件的覆盖

 public FileWriter(File file, boolean append) throws IOException
 讲解：加⼊true参数，会实现对⽂件的续写，使⽤false则会实现对⽂件的覆盖
 :::

 # 实战
 ```java
  public static void test1() throws IOException {
 String dir = "/Users/jack/Desktop/1.txt";
 FileWriter writer = new FileWriter(dir);
 writer.write(23567);
 writer.write(28404);
 writer.write(35838);
 writer.write(22530);
 writer.write("23567");
 writer.flush();
 writer.close();
 }
 public static void test1() throws IOException {
 String dir = "/Users/jack/Desktop/2.txt";
 FileWriter writer = new FileWriter(dir,true);
 writer.write(23567);
 writer.write(28404);
 writer.write(35838);
 writer.write(22530);
 writer.write("23567");
 writer.flush();
 writer.close();
 }
 ```