---
title: Java面向对象3(未完)
date: 2016-11-01 15:10:18
tags: [Java基础,day09]
categories: Java基础
description: Java面向对象笔记,内容包括:多态,抽象类,接口,day09
---

## 多态概述
- 多态:polymorphic 事物存在的多种形态
- 多态前提:
    + 要有继承关系;
    + 要有方法重写;
    + 要有父类引用指向子类对象;
- example
    + [多态案例](https://github.com/husthang/javaFoundation/tree/master/src/polymorphic)

## 多态中成员访问特点
- 访问成员变量
    + 编译看左边(父类),运行看左边(父类)
- 访问成员方法
    + 编译看左边(父类),运行看右边(子类).即动态绑定
- example
    + [动态绑定代码演示](https://github.com/husthang/javaFoundation/tree/master/src/polymorphic)
- reference
    + [多态讲解的博客](http://www.cnblogs.com/xdp-gacl/p/3644035.html)    

## 抽象类
- 概述及特点
- 抽象类的成员特点    
