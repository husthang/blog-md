---
title: Java面向对象2
date: 2016-10-21 10:32:07
tags: [Java基础,day08]
categories: Java基础
description: Java面向对象2笔记,包括:代码块,继承,final与super&&this关键字,重写和重载,day08
---

### 代码块

- 在java中,使用{}括起来的代码称为代码块;根据其位置和声明的不同,分为局部代码块,构造代码块,静态代码块,同步代码块(多线程)
- 应用
    + 局部代码块
        * 在方法中出现:限定生命周期,及早释放,提高内存利用率
    + 构造代码块(初始化快)
        * 在类中方法外出现:每次调用构造方法都执行,并且在构造方法前执行.
    + 静态代码块
        * 在类中方法外,并加上static修饰:用于给类初始化,随着类的加载而加载,且只执行一次(一般用来加载驱动)
- 面试题
```java
class Student{
    static {
        System.out.println("Student静态代码块");
    }
    {
        System.out.println("Student构造代码块");
    }
    public Student(){
        System.out.println("Student构造方法");
    }
}
class StudentTest{
    static {
        System.out.println("StudentTest静态代码块");
    }
    public static void main(String[]args){
        System.out.println("我是main方法");
        Student s1=new Student();
        Student s2=new Student();

    }
}
```
```bash
StudentTest静态代码块
我是main方法
Student静态代码块
Student构造代码块
Student构造方法
Student构造代码块
Student构造方法

Process finished with exit code 0
```

### 继承    

- Java中类的继承的特点
    + Java只支持单继承(一个儿子只能有一个爹)
    + Java支持多层继承
- 继承的好处
    + **让类与类之间产生了关系,是多态的前提**
    + 提高代码的复用性
- 继承的弊端
    + 类的耦合性增强
    + 开发的原则:高内聚,低耦合
    + 内聚:就是自己完成某件事情的能力
    + 耦合:类与类的关系
- Java继承的注意事项
    + 子类只能继承父类所有的非私有的成员
    + 子类不能继承父类的构造方法,但可以通过super去访问父类构造方法
    + 不要为了部分功能而去继承
- **继承中构造方法的关系**
    + 子类的构造方法中,一定要先调用父类的构造方法; 继承的目的,就是要继承父类的数据,可能还会使用父类的数据
    + 子类中的所有构造方法默认会访问父类中的空参数的构造方法(即默认加上 super();语句)
    + 子类初始化之前,一定要先完成父类的初始化 (有父才有子)
- this,super的应用和区别
    + 调用成员变量和成员方法
        * this.  调用本类或者调用父类的
        * super. 调用父类的
    + 调用构造方法
        * this(...)调用本类
        * super(...)调用父类的构造方法

-   
### final关键字

- 概述
    + 修饰类,方法及变量  最终
- final特点
    + 修饰类,类不能被继承
    + 修饰变量,则该变量只能赋值一次
    + 修饰方法,方法不能被继承  
- final修饰局部变量特点
    + 基本类型 值不能变
    + 引用类型 地址值不能变,对象中属性可以变   
- final 修饰变量的初始化
    + 最好显示初始化,不使用成员默认初始化值  

### Overload与Override

- Override 重写 子类中出现和父类中方法声明一模一样的方法,返回类型值一致
- Overload 重载 本类中出现的方法名一样,参数列表不同的方法,与返回类型值无关                             
