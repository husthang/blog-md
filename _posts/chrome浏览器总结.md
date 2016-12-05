---
title: chrome浏览器总结
date: 2016-11-14 13:55:20
tags: [chrome]
description: 总结chrome好用的插件,扩展,快捷键
categories: 奇技淫巧
---
## 快捷键篇
1. 参考[Chrome 键盘快捷键-mac](https://support.google.com/chrome/answer/157179?hl=zh-Hans)
2. 个人常用
    - 打开新窗口	⌘ + n
    - 打开新的标签页，并跳转到该标签页	⌘ + t
    - 关闭当前标签页或弹出式窗口	⌘ + w
    - 退出 Google Chrome 	⌘ + q
    - 打开“开发者工具”	⌘ + Option + i
    - 重新加载当前网页	 ⌘ + r
    - 开启或关闭全屏模式	⌘ + Ctrl + f
    - 跳转到地址栏	⌘ + l

## 插件篇   

## FAQ
1. chrome浏览器,地址栏搜索出现:无法访问,连接已经重置,与hosts文件无关
    用搜索框搜索出现链接重置,问题无关 hosts，在于链接是http方式访问。搜索框输入 chrome://net-internals/#hsts
    在 Input a domain name to add it to the HSTS set: 这一行下面的 Domain: [ ]
    输入 www.google.com.hk 点 Add这个方法可以让 Chrome 访问 www.google.com.hk 时，强制选择 https 方式
    [参考](https://github.com/racaljk/hosts/issues/387)
