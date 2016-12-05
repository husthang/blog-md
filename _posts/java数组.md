---
title: java数组
date: 2016-10-18 14:51:28
tags: [Java基础,day05]
categories: Java基础
description: java数组,java内存分配,笔记,day05
---

### 数组概述

- 数组作用
    + 为了存储同种数据类型的多个值
- 数组概念
    + 数组是存储统一数据类型的多个元素的集合
    + 数组既可以存储基本数据类型,也可以存储引用数据类型
- 数组定义格式
    + 数据类型[]数组名=new 数据类型[数组长度];
```java
int[]arr=new int[5];
```

### 数组的静态初始化,动态初始化
- 什么是数组初始化
    + 就是为数组开辟连续的内存空间,并为每个数组元素赋值
- 初始化方法
    + 静态初始化:给出初始化值,由系统决定长度
```java
    int[]arr={1,2,3,4};//不可拆开,声明和赋值在同一行,不可写为:int[]arr;arr={1,2,3};
    int[]arr=new int[]{1,2,3,4};//可拆开写,先声明后赋值;
```
    + 动态初始化:只指定长度,由系统给出初始化值
```java
    int[]arr=new int[5];
```
- ***数组动态初始化,系统默认初始化值***
    + 整型数组(byte,short,int,long),默认初始化值为0;
    + 浮点型(float,double),默认初始化值为0.0;
    + 布尔型(boolean),默认初始化值为false;
    + 字符型(char):默认初始化值为'\u0000',char在内存中两个字节,16位,\u转移序列符为Unicode编码

```java
public class ArrayTest{
    public static void main(String[]args){
        int[]arr=new int[5];
        System.out.println(arr[0]);
        arr[0]=10;
        System.out.println(arr[0]);
        System.out.println(arr);
    }
}
```
```bash
0
10
[I@7852e922
[Finished in 1.6s]
```

+ example解释:[I@7852e922
    * [代表数组,几个就代表几维
    * I代表int型
    * @是固定的
    * 7852e922代表16进制的地址

### Java中的内存分配以及栈和堆的区别

- 栈
    + 存储局部变量和方法调用
        * 局部变量:定义在方法声明上和方法中的变量
- 堆
    + 存储new出来的数组或对象
- 方法区
    + 代码区(见面向对象部分)
- 本地方法区
    + 和系统相关
- 寄存器
    + 给CPU使用
- ***堆主要用来存放对象的，栈主要是用来执行程序的***

### 深入分析java中的length和length()

- 问题
```java
int[] arr = new int[3];
System.out.println(arr.length);//使用length获取数组的程度

String str = "abc";
System.out.println(str.length());//使用length()获取字符串的长度
```
    + 为什么数组有length属性，而字符串没有？
- 分析
    + 详见这篇文章 <http://www.hollischuang.com/archives/1261>
    + 数组length理解为其属性
```java
Object obj = new int[3];//本句合法
int[] arr = new int[3];
System.out.println(arr.getClass());//输出为 class [I
```
