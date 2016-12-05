---
title: html笔记
date: 2016-10-21 10:58:12
tags: [JavaWeb,html]
categories: JavaWeb
description: JavaWeb基础学习笔记,html
---

### html简介

- html含义
    + Hyper Text Markup Language 超文本标记语言
    + 不是编程语言,是一套标签
    + 超文本
        * 能实现普通文本不能实现的功能
        * 包括超链接的文本
    + 标记
        * 就是标签,不同标签实现不同功能
    + 语言
        * 人与计算机交互的工具

### html书写规范

- html不区分大小写,建议用小写
```html
<html>
    <head>
        包括整个页面属性,指导浏览器解析的标签,引入外部文件的标签
    </head>
    <body>
        主体,要展示的信息
    </body>
<html>
```

### html基本标签

- 文件标签(结构标签)
    + <html></html>根标签
    + <body></body>内容
- 排版标签
    + 注释 `<!--注释-->`
    + 换行 `<br/>`
    + 段落 `<p>文本文字</p>`
        * 段落之间有空行;属性: align:left,center,right
    + 水平 `<hr/>`    
- 块标签
    + `<div></div>`
    + `<span></span>`
- 文字标签
    + `<font></font>`
    + `<h1></h1>-<h6>`
- 清单标签
    + 无序列表 `<ul></ul>; <li></li>`列表项
    + 有序列表 `<ol></ol>`
```html
<ul>
    <li>列表项</li>
    <li>列表项</li>
<ul>
```    
- 图形标签
    + `<img/>` (自关闭标签)
- 链接标签
    + `<a></a>`

### html表单标签

- form标签:`<form></form>`
    + 属性
        * ame:表单名称
        * action:提交的路径地址
        * method:提交的方式
            - get提交：将提交的数据加在地址栏的后面，提交大小有限制
            - post提交：将数据封装在请求体中
        
- input标签
    + 属性
        * type: 根据type值不同,显示不同功能的表单项;
            - text:普通的文本输入框
            - password: 密码输入框
            - radio: 单选按钮. 注意:组的概念,如果想让一组单选按钮互斥,必须name属性值相同
            - checkbox: 复选框
            - file:上传文件
            - button: 普通按钮,无内置功能
            - submit:提交按钮,点击后表达安装action地址进行提交
            - reset: 重置
            - image:图片按钮,src代表图片地址,alt代表图片的提示文字信息,内置功能同submit
            - hidden: 隐藏表单，在提交数据的时候，服务器需要这个数据，但不需要用户看到
        * name和value属性是提交到后台的，对应 键-值
- select标签
- textarea标签(文本域标签)    
    + 属性
        * col 列数
        * row 行数