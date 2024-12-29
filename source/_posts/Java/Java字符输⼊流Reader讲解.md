---
title: Java字符输⼊流Reader讲解
date: 2021/09/22 20:22:00
tags:
  - Tag
categories:
  - Java
---

# Reader是输⼊字符流的⽗类，它是⼀个抽象类, 部分库不推荐使⽤Reader/Writer
:::info
int read()
讲解：⼀个字符⼀个字符的读,只能⽤来操作⽂本(不能写图⽚ ⾳频 视频)

int read(char cbuf[])
讲解：从输⼊字符流中读取⼀定数量的字符，并将其存储在缓冲区数组cbuf中, 返回实际读取的字符数，如果已经到达流末尾⽽没有可⽤的字节，则返回－1

void close() throws IOException
讲解：关闭输⼊流并释放与该流关联的系统资源
:::

# 常⻅⼦类
FileReader ⽤来读取字符⽂件的实现类
```java
public FileReader(String fileName) throws FileNotFoundException {
 super(new FileInputStream(fileName));
}
public FileReader(File file) throws FileNotFoundException {
 super(new FileInputStream(file));
}
```
# 实战
```java
//读取中⽂显示出来, java运⾏时采⽤utf16编码，多数汉字占2个字节，⼀个char就够，少数占4个
字节，需要两个char来表示
 public static void test1() throws IOException {
 String dir = "/Users/jack/Desktop/1.txt";
 File file = new File(dir);
 Reader input = new FileReader(file);
 int ch;
 //最后取值到-1的情况
 while ((ch = input.read()) != -1) {
 System.out.print((char)ch);
 }
 input.close();
 }

public static void test2() throws IOException {
 String dir = "/Users/jack/Desktop/1.txt";
 File file = new File(dir);
 Reader input = new FileReader(file) ;
 char c[] = new char[1024] ; //⼀次性读取
 int len = input.read(c) ;
 //关闭输出流
 input.close() ;
 System.out.println("内容为：" + new String(c,0,len)) ; // 把字符数组变为
字符串输出
}
```