---
title: Java基础概述
date: 2016-10-15 22:19:14
tags: [Java基础,day01]
categories: Java基础
description: Java基础,day01笔记.
---

## Java语言概述（了解）
* A:Java语言发展简史
    James Gosling,Patrick,Mike Sheridan等,由"Green计划",开始叫"Oak",后改名Java.
    Java取名来源:Oak被注册,java本来含义为一个岛名"爪洼岛",这个岛盛产咖啡.
    SUN公司:Stanford University Network,斯坦福大学网络公司
* B:Java语言版本
    *
* C:Java语言平台
    * 跨平台
    * 面向对象
    * 自动垃圾回收
    * 解释性
    * 多线程
    * 分布式处理
* D:Java语言平台版本
    * J2SE(Java 2 Platform Standard Edition)标准版, 即java的基础,是下面两版的基础
    * J2ME(Java 2 Platform Micro Edition)小型版,电子消费产品和嵌入式设备用的,现在用的很少了
    * J2EE(Java 2 Platform Enterprise Edition)企业版 ,开发企业环境应用程序,主要针对Web应用程序开发

## Java语言跨平台原理（掌握）
* A:什么是跨平台
    write once,run anywhere!
    通过Java语言编写的应用程序,在不同的系统平台上都可以运行.即良好的可移植性,Java应用程序源代码不用改.
* B:Java跨平台原理
    * 只要在需要运行Java应用程序的操作系统上，安装一个Java虚拟机（JVM java virtual machine）。由jvm负责java程序在该系统中的运行

## JRE和JDk（掌握）
* A:什么是JRE
    * java runtime environment. Java运行环境，包括JVM和Java程序所需的核心类库,运行已经开发好的Java程序,只需安装了JRE即可
* B:什么是JDK
    * Java Development Kit. Java开发包
    * JDK供开发人员使用,包含Java开发工具,也包含JRE;

## Java标识符(掌握)
* A:什么是标识(zhi)符
    - 就是给类,接口,方法,变量起名字时使用的字符序列
* B:标识符的组成规则
    - 以字母开头的,由字母或者数字构成的序列
    - 包括'_','$'
    - 大小写敏感,变量名长度没有限制
    - 不能是java当中的关键字,不能有空格
* C:标识符常见命名规则
    - 包:域名的倒序,所有字母小写
    - 类or接口:
        * 如果是一个单词,首字母大写;
        * 多个单词,则每个单侧首字母大写(驼峰标识)
    - 方法or变量
        * 如果是一个单词,全部小写
        * 如果多个单词,从第二个单词首字母大写
    - 常量
        * 一个单词,所有字母大写
        * 多个单词,所有单词大写,单词之间用下划线间隔

## Java关键字
* A:什么是关键字
    * 被java语言赋予特定含义的单词
* B:特点
    * 组成关键字的字母全部小写
    * goto和const作为保留关键字存在,目前并不使用

## Java文件名与类名

* 一个java文件中,可以有多个类(编译后,每个类都会生成一个.class文件),但是最多只能有一个public类,如果有public类,则java文件名必须与此public类名保持一致.
