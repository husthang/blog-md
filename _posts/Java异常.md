---
title: Java异常
date: 2016-11-09 17:12:44
tags: [Java异常,Java基础,day19]
description: Java异常总结,day19
categories: Java基础
---
## 异常分类
- Java中的异常层次结构
    + Throwable
        * Error
        * Exception
            - RuntimeException : 由程序错误导致的异常,包含这几种情况: 错误的类型转换; 数组访问越界; 访问空指针;
            - 其他Exception:  包括情况: 试图在文件尾部后面读取数据; 试图打开一个不存在的文件; 试图根据给定的字符串查找Class对象,而该字符串表示的类并不存在;
- 出现RuntimeException 则一定是程序员的问题
- 将派生于Error类或者RuntimeException类的所有异常,称为**未检查异常**
- 其他Exception称为**已检查异常**, 需要程序员显示声明(throws)或者捕获(try,catch),不然不能通过编译

## 异常的处理
- 异常处理的两种方式
    + a: try..catch..finally 捕获并处理异常
    + b: throws: 声明异常,交给该方法的调用者来处理
        * 跟在方法声明后面,表示抛出异常.
        * 声明抛出异常,由该方法的调用者来处理
        * 方法体内里通过`throw`抛出异常,则方法声明中要用`throws`声明.
- 注意事项
    + 原则: 如果方法内部可以将问题处理,用try处理; 如果处理不了,用throws在方法上声明有异常,交由方法的调用者处理.
    + 区别: 后续程序需要继续运行,则用try catch处理; 后续程序不需要继续运行,就用throws处理   
- 方法重写注意
    + 子类重写方法时,如果父类方法抛出多个异常,子类方法只能抛出父类异常的子集; 子类方法只能抛出父类异常相同的类或者子类.
## finally关键字
- 被finally控制的语句体一定会执行(特殊: 执行到finally之前,jvm退出了,比如遇到了`System.exit(0);`)
- finally作用: 用于释放资源,例如IO和数据库操作中
```java
public class ExceptionDemo3 {
    public static void main(String[] args) {
        try{
            System.out.println(10/0);
        }catch (Exception e){
            System.out.println("除数为零");
            //System.exit(0);
            return;
        }finally {
            System.out.println("是否执行");//有return语句也会执行;碰到exit(0),jvm提前退出,则不执行
        }
    }
}
```
## 自定义异常
- 使用自定义异常的步骤
    + 1.通过继承`java.lang.Exception`声明自己的异常类
    + 2.在方法的适当位置,生成自定义异常的实例,并用throw语句抛出
    + 3.在方法声明部分,用throws声明异常

## 练习demo
- [ExceptionDemo](https://github.com/husthang/javaFoundation/tree/master/src/exception)
- 博客推荐: [孤傲苍狼博客java异常](http://www.cnblogs.com/xdp-gacl/p/3627390.html)
