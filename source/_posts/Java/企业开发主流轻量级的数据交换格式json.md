---
title: 企业开发主流轻量级的数据交换格式json
date: 2021/10/01 15:15:00
tags:
  - Tag
categories:
  - Java
---

# 什么是JSON
JSON(JavaScript Object Notation, JS 对象简谱) 是⼀种轻量级的数据交换格式 
好处:
简洁和清晰的层次结构使得 JSON 成为理想的数据交换语⾔ 易于⼈阅读和编写，同时也易于机器解析和⽣成，并有效地提升⽹络传输效率 JSON 独⽴于语⾔和平台，JSON 解析器和 JSON 库⽀持许多不同的编程语⾔

# 格式 key value 键值对
花括号保存对象 {"key":"value"} ⽅括号保存数组[{"key":"value"},{"key":"value"}]
值类型 
数字（整数或浮点数） 
字符串（在双引号中） 
逻辑值（true 或 false） 
数组（在⽅括号中） 
对象（在花括号中） null

# 什么是json字符串
json对象被序列化为字符串，就叫json字符串，和对象可以互相转换