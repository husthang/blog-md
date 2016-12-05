---
title: css笔记
date: 2016-10-25 17:09:38
tags: [JavaWeb,css]
description: css笔记
categories: JavaWeb
---

### css简介

- 什么是css
    + 层叠样式表 Cascading Style Sheets
    + 对html进行样式修饰
    + 层叠： 就是层层覆盖叠加
    + 样式表： 属性的集合
- css引入方式和书写规范
    + 内嵌样式
        * 语法： 使用style属性嵌入html标签;属性写法 属性：属性值 多个属性间，用分号隔开
        * example: `<div style="color:red;font-size: 50px;">你好</div>`
    + 内部样式
        * 在head标签中使用style标签进行css的引入
        * example:
        ```html
            <style type="text/css">
                div{color:red;font-size: 50px}
            </style>
        ```
    + 外部样式
        * 将css样式抽取成一个单独的文件,在head标签中，用link引入
        * example： `<link rel="stylesheet" type="text/css" href="demo.css">`
    + @import方式

### css选择器

- 基本选择器
    + 元素选择器
        * 语法 `html标签名{css属性}`
        * example `span{color:red}`
    + id选择器
        * 语法 `#id值{css属性}`
        * id唯一性
    + class选择器
        * 语法 `.class值{css属性}`
    + 选择器的优先级：id>class>元素
- 属性选择器
    + 语法 `基本选择器[属性='属性值']{css属性}`
    + example
    ```html
        <form>
            name:<input type="text">
            pass:<input type="password">
        </form>
        <style type="text/css">
            input[type='text']{background: yellow}
            input[type='password']{background:pink}
        </style>
    ```
- 伪元素选择器
    + a标签的伪元素选择器，语法 
        * 静止状态 a:link{}
        * 悬浮状态 a:hover{}
        * 触发状态 a:active{}
        * 完成状态 a:visited{]
        ```html
            <a href="#">点击我吧</a>
            <style type="text/css">
                a:link{color:blue}
                a:hover{color:red}
                a:active{color:yellow}
                a:visited{color:green}
            </style>
        ```
- 层级选择器
    + 语法： 父级选择器 子级选择器
    + example:
    ```html
     <div id="d1">
            <div class="dd1">
                <span>span1-1</span>
            </div>
            <div class="dd2">
                <span>span1-2</span>
            </div>
        </div>
        <div id="d2">
            <div class="dd1">
                <span>span1-1</span>
            </div>
            <div class="dd2">
                <span>span1-2</span>
            </div>
        </div>
        <style type="text/css">
            #d1 .dd2 span{color:red}
        </style>
    ```

### css属性    