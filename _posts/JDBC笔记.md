---
title: JDBC笔记
date: 2016-11-07 14:59:13
tags: [JavaWeb,JDBC]
description: JDBC学习笔记
categories: JavaWeb
---
##  JDBC概述
- java database connectivity
- JDBC规范(掌握四个核心对象)
    + DriverManager: 用于注册驱动
    + Connection: 表示与数据库创建的连接
    + Statement: 操作数据库的sql语句的对象
    + ResultSet: 结果集或者一张虚拟表
- 步骤
    + 注册驱动
    + 创建连接
    + 得到执行sql语句的Statement对象
    + 执行sql语句,返回结果
    + 处理结果
    + 关闭资源
- example
    + [jdbc demo](https://github.com/husthang/javaWebFoundation/tree/master/jdbc_study)

## JDBC常用的类和接口详解
- 注册驱动(加载驱动)    
    + `DriverManager.registerDriver(new com.mysql.jdbc.Driver());`不建议使用. 内部又注册了一次
    + 建议使用: `Class.forName("com.mysql.jdbc.Driver");`
- 与数据库建立连接
    + URL:sun公司与数据库厂商的协议
        - jdbc:mysql://localhost:3306/study
        - 协议 子协议    ip    端口号   数据库
- sql注入问题
    + 用 preparedStatement 先编译sql语句        