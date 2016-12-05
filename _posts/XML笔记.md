---
title: XML笔记
date: 2016-11-11 10:33:48
tags: [XML,JavaWeb]
description: XML学习笔记
categories: JavaWeb
---
## XML概述
- XML: extensible Markup Language 可扩展标记语言
- 可扩展:所有的标签是自定义的
- 功能:数据存储
    * 配置文件
    * 数据传输
- html和xml区别
    * html语法松散,xml语法严格
    * html做页面展示,xml做数据存储
    * html所有标签是预定义,xml标签是自定义
- W3C: World Wide Web Consortium 万维网联盟    

## XML语法
- 文档声明
    + 必须写在xml文档的第一行
    + 写法: `<?xml version="1.0" ?>`
    + 属性
        * version: 版本号,固定值1.0
        * encoding: 文档编码
        * standalone: 指定文档是否独立 yes或no
- 元素
    + 文档中必须有且只能有一个根元素
    + 元素名称:
        + 元素名称区分大小写
        + 数字不能开头

## XML约束
- 约束就是xml的书写规则
- 约束分类
    + dtd: Document Type Definition.
        * 内部dtd: 在xml内部定义dtd
        * 外部dtd: 在外部定义dtd:
    + schema:
        * 导入xsd约束文档
            1. 编写跟标签
            2. 引入实例命名空间 xmlns:xsi=""
            3. 引入名称空间 xsi:schemaLocation=""
            4. 引入默认的名称空间
