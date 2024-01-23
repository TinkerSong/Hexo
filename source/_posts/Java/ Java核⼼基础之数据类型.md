---
title: Java核⼼基础之数据类型
date: 2021/08/17 20:34:00
categories:
- [Java]
valine:
  placeholder: "本文档为学习笔记，祝食用愉快💪"
---

# 简介：讲解Java内置数据类型
## 计算机基础知识
:::info
bit 位 ,即0或者1, 0101010110
byte字节，8位作为⼀个字节，字节是处理数据的基本单位
1 byte = 8bits
1KB = 1024 bytes
1MB = 1024 KB
1GB = 1024 MB
:::

## ⼋种基本数据类型（每个数据都需要从计算机内存中申请空间，来存储它）
:::info
byte
8位
最⼤127，最⼩-128
节省空间，占⽤int类型的四分之⼀
默认 0

short
16位
最⼩-32768，最⼤32767
int类型的⼆分之⼀
默认是0

int
32位
最⼩ -2147483648，最⼤ 2147483647
整数默认是int类型
默认是0

long
64位
最⼩ -9223372036854774808，最⼤ 9223372036854774807
默认是 0L,
float 浮点
单精度32位
默认0.0f

double
双精度 64位
浮点数默认位double类型
默认是0.0

boolean
1位
true或者false
默认是false

char
16位的 unicode字符，即两个字节表示⼀个字符
最⼩是 \u0000 即0，做⼤ \ufff 即65535
例⼦ char demo = 'A'

类型转换 double > float > long > int > short > byte

引⽤数据类型：Class创建的对象 或者 数组都是引⽤数据类型
String ：字符串对象，也是引⽤数据类型
:::