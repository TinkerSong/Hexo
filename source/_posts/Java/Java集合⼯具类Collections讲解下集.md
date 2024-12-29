---
title: Java集合⼯具类Collections讲解下集
date: 2021/09/14 21:14:00
tags:
  - Tag
categories:
  - Java
---

# 方法
1. 获取最⼤元素 max(Collection coll) 默认⽐较，不适合对象⽐较
2. 获取最⼤元素 max(Collection coll, Comparator comparator)
```java
public class CollectionsTest {
 public static void main(String[] args) {
 List<Student> list = new ArrayList<>();
 list.add(new Student("jack", 26));
 list.add(new Student("tom", 29));
 list.add(new Student("mary", 32));
 list.add(new Student("tony", 19));
 list.add(new Student("smith", 41));
 System.out.println(list);
 Student maxAgeStudent = Collections.max(list, new
Comparator<Student>() {
 @Override
 public int compare(Student o1, Student o2) {
 return o1.getAge() - o2.getAge();
 }
 });

 Student mixAgeStudent = Collections.mix(list, new
Comparator<Student>() {
 @Override
 public int compare(Student o1, Student o2) {
 return o1.getAge() - o2.getAge();
 }
 });
 System.out.println(maxAgeStudent.toString());
 }
}
class Student {
 public Student(String name, int age) {
 this.name = name;
 this.age = age;
 }
 private int age;
 private String name;
 public void setAge(int age) {
 this.age = age;
 }
 public int getAge() {
 return age;
 }
 public void setName(String name) {
 this.name = name;
 }
 public String getName() {
 return name;
 }
 @Override
 public String toString() {
 return "Student{" +
 "age=" + age +
 ", name='" + name + '\'' +
 '}';
 }
}

获取最⼩元素 min(Collection coll)
创建不可变集合unmodifiablleXXX()
```java
List<String> list = new ArrayList<>();
 list.add("SpringBoot课程");
 list.add("架构课程");
 list.add("微服务SpringCloud课程"); //设置为只读List集合
 list = Collections.unmodifiableList(list);
 System.out.println(list);
 Set<String> set = new HashSet<>();
 set.add("Mysql教程");
 set.add("Linux服务器器教程");
 set.add("Git教程");
 //设置为只读Set集合
 set = Collections.unmodifiableSet(set);
 System.out.println(set);
 Map<String, String> map = new HashMap<>();
 map.put("key1", "课程1");
 map.put("key2", "课程2");
 //设置为只读Map集合
 map = Collections.unmodifiableMap(map);
 System.out.println(map);
 ```