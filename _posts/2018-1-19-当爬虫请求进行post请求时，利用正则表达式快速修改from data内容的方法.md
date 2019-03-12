---
layout:     post
title:      当爬虫请求进行post请求时，利用正则表达式快速修改from data内容的方法
subtitle:   本文利用atom软件进行修改，其他软件亦可
date:       2018-1-19
author:     WHY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - 正则表达式
    - 爬虫
    - post请求
---

## From Date内容

![from data](https://github.com/ErDangJia0/ErDangJia0.github.io/blob/master/img/%E5%BD%93%E7%88%AC%E8%99%AB%E8%AF%B7%E6%B1%82%E8%BF%9B%E8%A1%8Cpost%E8%AF%B7%E6%B1%82%E6%97%B6%EF%BC%8C%E5%88%A9%E7%94%A8%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E5%BF%AB%E9%80%9F%E4%BF%AE%E6%94%B9from%20data%E5%86%85%E5%AE%B9%E7%9A%84%E6%96%B9%E6%B3%95/data%E5%86%85%E5%AE%B9.jpg?raw=true)

## JSON格式

![json格式](https://github.com/ErDangJia0/ErDangJia0.github.io/blob/master/img/%E5%BD%93%E7%88%AC%E8%99%AB%E8%AF%B7%E6%B1%82%E8%BF%9B%E8%A1%8Cpost%E8%AF%B7%E6%B1%82%E6%97%B6%EF%BC%8C%E5%88%A9%E7%94%A8%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E5%BF%AB%E9%80%9F%E4%BF%AE%E6%94%B9from%20data%E5%86%85%E5%AE%B9%E7%9A%84%E6%96%B9%E6%B3%95/json%E6%A0%BC%E5%BC%8F.jpg?raw=true)

## 利用ATOM软件及正则表达式进行替换修改

首先将内容复制至ATOM新建文件内，点击上方查找，替换，然后在下方查找框写入

`^(.*):(.*)$`

在替换框内输入

"$1":"$2",

$1和$2分别代表查找框内括号内的内容，点击全部替换后，搞定！！！！

![替换](https://github.com/ErDangJia0/ErDangJia0.github.io/blob/master/img/%E5%BD%93%E7%88%AC%E8%99%AB%E8%AF%B7%E6%B1%82%E8%BF%9B%E8%A1%8Cpost%E8%AF%B7%E6%B1%82%E6%97%B6%EF%BC%8C%E5%88%A9%E7%94%A8%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F%E5%BF%AB%E9%80%9F%E4%BF%AE%E6%94%B9from%20data%E5%86%85%E5%AE%B9%E7%9A%84%E6%96%B9%E6%B3%95/%E6%9B%BF%E6%8D%A2.jpg?raw=true)

##### 很方便是不是，小技巧改变生活。

