---
title: Java输⼊流InputStream讲解
date: 2021/09/20 22:22:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# InputStream是输⼊字节流的⽗类，它是⼀个抽象类（⼀般⽤他的⼦类）
:::info 
int read()
讲解：从输⼊流中读取单个字节,返回0到255范围内的int字节值,字节数据可直接转换为int类
型, 如果已经到达流末尾⽽没有可⽤的字节，则返回－1

int read(byte[] buf)
讲解：从输⼊流中读取⼀定数量的字节，并将其存储在缓冲区数组buf中, 返回实际读取的字节
数，如果已经到达流末尾⽽没有可⽤的字节，则返回－1

long skip(long n)
讲解：从输⼊流中跳过并丢弃 n 个字节的数据。

int available()
讲解：返回这个流中有多少个字节数，可以把buf数组⻓度定为这个

void close() throws IOException
讲解：关闭输⼊流并释放与该流关联的系统资源
:::

# 常⻅⼦类
FileInputStream
1. 抽象类InputStream⽤来具体实现类的创建对象, ⽂件字节输⼊流, 对⽂件数据以字节的形式进⾏读取操作
2. 常⽤构造函数
```java
//传⼊⽂件所在地址
public FileInputStream(String name) throws FileNotFoundException
//传⼊⽂件对象
public FileInputStream(File file) throws FileNotFoundException
```
3. 实战
```java
public static void main(String[] args) throws IOException {
 String dir ="C:\\Users\\79466\\Desktop;
 String name = "a.txt";
 File file = new File(dir, name);
 InputStream inputStream = new FileInputStream(file);
 testReadByteArr(inputStream);
 }
 public static void testRead(InputStream inputStream) throws
IOException {
 //对于汉字等unicode中的字符则不能正常读取,只能以乱码的形式显示
 int read = inputStream.read();
 System.out.println(read);
 System.out.println((char) read);
 }
 public static void testSkip(InputStream inputStream) throws
IOException {
 long skipSize = inputStream.skip(2);
 System.out.println(skipSize);
 int read = inputStream.read();
 System.out.println(read);
 System.out.println((char) read);
 }
 public static void testReadByteArr(InputStream inputStream)
throws IOException {
 //如果 buf 的⻓度为 0，则不读取任何字节并返回 0； 每次读取的字节数最多
等于buf 的⻓度;
 byte[] buf = new byte[1024];
 int length;
 //循环读取⽂件内容，输⼊流中将最多buf.length个字节的数据读⼊⼀个buf数
组中,返回类型是读取到的字节数。
 //如果这个缓冲区没有满的话，则返回真实的字节个数
 //当⽂件读取到结尾时返回 -1,循环结束
 while ((length = inputStream.read(buf)) != -1) {
 System.out.print(new String(buf, 0, length));
 //中⽂乱码问题，换成GBK 或者 UTF-8
 //System.out.println(new String(buf,"UTF-8"));
 //System.out.println(new String(buf,0, length,"UTF-8"));
 //System.out.println(new String(buf, 0, length));
 }
 //最后记得关闭流
 inputStream.close();
 }
```

ByteArrayInputStream 字节数组输⼊流
ObjectInputStream 对象输⼊流

# 编码⼩知识（节省空间）
1. 操作的中⽂内容多则推荐GBK：
GBK中英⽂也是两个字节,⽤GBK节省了空间,
UTF-8 编码的中⽂使⽤了三个字节
2. 如果是英⽂内容多则推荐UFT-8:
因为UFT-8⾥⾯英⽂只占⼀个字节
UTF-8编码的中⽂使⽤了三个字节
3. 编码知识拓展：
https://baike.baidu.com/item/UTF-8/481798?fr=aladdin
https://baike.baidu.com/item/GBK%E5%AD%97%E5%BA%93?fromtitle=GBK&fromi
d=481954