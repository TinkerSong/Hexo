---
title: ⽹络请求http基础知识讲解
date: 2021/10/01 14:45:00
tags:
  - Tag
categories:
  - Java
---

# 说明
不讲解TCP/IP、ISO七层⽹络模型、Socket通信、TCP 三次握⼿四次挥⼿等底层知识
# 协议 
协议是⼀种约定，规定好⼀种信息的格式，如果发送⽅按照这种请求格式发送信息，那么接收端就要按照这样的格式解析数据，这就是协议

# ⽹络由下往上分为物理层、数据链路层、⽹络层、传输层、会话层、表示层和应⽤层。
1. IP协议对应于⽹络层
2. TCP协议对应于传输层
3. HTTP协议对应于应⽤层， 还有FTP、TELNET等

:::info 
* 重点
 TPC/IP协议是传输层协议，主要解决数据如何在⽹络中传输
 HTTP是应⽤层协议，主要解决如何包装使⽤数据，由请求和响应构成
:::

# 什么是HTTP协议 
HTTP协议即超⽂本传送协议(Hypertext Transfer Protocol )，是Web联⽹的基础，也是⼿机PC联⽹常⽤的协议之⼀，HTTP协议是建⽴在TCP协议之上的⼀种应⽤。HTTP连接最显著的特点是客户端发送的每次请求都需要服务器回送响应，从建⽴连接到关闭连接的过程称为“⼀次连接”
1. HTTP请求

2. HTTP响应
响应码： 1xx:信息 2xx:成功 200 OK，请求正常 3xx:重定向 4xx:客户端错误 404 Not Found
服务器⽆法找到被请求的⻚⾯ 5xx:服务器错误 503 Service Unavailable，服务器挂了或者不
可⽤

3. 查看常⻅的站点 taobao.com , baidu.com

# 什么是URL（统⼀资源定位符）
:::info 
标准格式: 协议://服务器IP:端⼝/路径1/路径N ? key1=value1 & key2=value2
协议：不同的协议有不同的解析⽅式
服务器ip: ⽹络中存在⽆数的主机,要访问的哪⼀台, 通过公⽹ip区分
端⼝: ⼀台主机上运⾏着很多的进程，为了区分不同进程，⼀个端⼝对应⼀个进程，http默认的端⼝是80
路径: 资源N多种，为了更进⼀步区分资源所在的路径（后端接⼝，⼀般称为 “接⼝路径”，“接⼝”）
:::