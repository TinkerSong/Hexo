---
title: Java集合元素排序接⼝Comparable讲解
date: 2021/09/14 21:14:00
tags:
  - Tag
categories:
  - Java
---

# 什么是Comparable
```java
public interface Comparable<T> {
 public int compareTo(T o);
}
```
1. 是⼀个接⼝，定制排序规则
2. 对实现它的每个类的对象进⾏整体排序，⾥⾯ compareTo ⽅法是实现排序的具体⽅法
3. ⽐如TreeSet、SortedSet、Collections.sort() ⽅法调⽤进⾏排序
4. String、Integer等类默认实现了这个接⼝，所以可以排序(看源码)

# 详解compareTo⽅法
1. ⽤于⽐较次对象和指定对象的顺序，o为要⽐较的对象
2. 返回int类型
⼤于0, 表示this⼤于传进来的对象o ,则往后排，即升序
等于0，表示this等于传进来的对象o
⼩于0，表示this⼩于传进来的对象o

# 需求：根据学⽣的年龄进⾏排序
```java
public class TestCom {
 public static void main(String [] args) {
 Set<Student> studentSet = new TreeSet<>();
 studentSet.add(new Student("jack",32));
 studentSet.add(new Student("tom",22));
 studentSet.add(new Student("mary",35));
 studentSet.add(new Student("tim",11));
 studentSet.add(new Student("tony",49));
 studentSet.add(new Student("dd",30));
 System.out.println(studentSet);
 }
}
 class Student implements Comparable{
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
 public Student(String name,int age){
 this.name = name;
 this.age = age;
 }
 @Override
 public String toString() {
 return "Student{" +
 "age=" + age +
 ", name='" + name + '\'' +
 '}';
 }
 @Override
 public int compareTo(Object o) {
 if(o instanceof Student){
 Student student = (Student)o;
 return this.age - student.age;
 }
 //返回的数是0代表两个对象相同
 return 0;
 }
}
```
