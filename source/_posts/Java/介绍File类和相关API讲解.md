---
title: 介绍File类和相关API讲解
date: 2021/09/20 20:22:00
tags:
  - Tag
categories:
  - Java
---

# 程序代码和⽂件⽬录的关系：主要就是对⽂件和⽬录进⾏增删改查，俗称CRUD

# 简单了解IO，即Input/Output
1. 把内存的中数据存储到持久化设备到上的动作称为输出，Output 操作
2. 把持久化设备的数据读取到内存中的动作称为输⼊，Input操作
3. ⼀般把输⼊和输出的动作称为IO操作，IO也分⽹络IO，⽂件IO

# java⽂件类File：
1. 主要是计算机⽂件和⽬录的操作，即对⽂件的和⽬录的增删改查
2. File类表示磁盘中存在的⽂件和⽬录
3. File类的包名是java.io，也实现了Serializable, Comparable两⼤接⼝以便于其对象可序列化和⽐较
4. File.separator ⽬录分隔符，在不同的系统下不⼀样, windows和 mac /Linux

# 常⻅的构造函数
```java
//路径和⽂件拼接
public File(String pathname)
//⽗路径，⼦路径
public File(String parent, String child)
//测试⽅法：⽂件的路径，即new File构造函数传⼊的路径
String getPath()
```

# 常⻅⽅法
```java
String dir = "C:\\Users\\79466\\Desktop\\;
 String name = "a.txt";
 File file = new File(dir, name);
 //File file = new File(dir);
 //⽂件的 查询和判断
 System.out.println(File.separator);
 System.out.println("基本路径 getPath()= " + file.getPath());
 System.out.println("⽂件名 getName()= " + file.getName());
 System.out.println("绝对路径 getAbsolutePath = " +
file.getAbsolutePath());
 System.out.println("⽗路径名 getParent() = " + file.getParent());
 System.out.println("是否是绝对路径 isAbsolute() = " +
file.isAbsolute());
 System.out.println("是否是⼀个⽬录 isDirectory() = " +
file.isDirectory());
 System.out.println("是否是⼀个⽂件 isFile() = " + file.isFile());
 System.out.println("⽂件或⽬录是否存在 exists() = " +
file.exists());
 System.out.println("⽬录中的⽂件和⽬录的名称所组成字符串数组 list() ");
 String[] arr = file.list();
 for (String temp : arr) {
 System.out.println(temp);
 }
 //创建指定的⽬录
 File mkdirFile = new File(dir + "/testdir");
 mkdirFile.mkdir();
 //创建多个层级的⽬录
 File mkdirsFile = new File(dir + "/testdirs/test/dd");
 mkdirsFile.mkdirs();
// //创建⼀个新的⽂件
 File newFile = new File(dir + "/testdir/newfile1.txt");
 try {
 newFile.createNewFile();
 } catch (IOException e) {
 e.printStackTrace();
 }
 //删除⽂件
 newFile.delete();
 ```

 # 注意
 File的构造函数只是创建⼀个File实例，即使⽬录错误也不出报错，因为没对⽂件进⾏操作