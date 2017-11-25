---
layout: blog
title: JavaScript高级程序设计第三版（读后感）（第一篇）
date: 2017-11-25 11:01:05
categories: professional_javascript_for_web_develop_3rd
tags: JavaScript-web-develop-3rd
---
# JavaScript高级程序设计第三版（读后感）（第一篇）
> 《JavaScript高级程序设计第三版》nichoals C.Zakes 著。此书2012年出版。囊括了基本概念、语言核心、面向对象、BOM、DOM、事件模型、Canvas、...。还引用了当时的刚刚发布不久的html5、ECMAScript 5。

# 概览
本书囊括了25章节。附录4篇。可以算的上是一本权威指南书了。包含了JavaScript语言99%的内容。本书提供给JavaScript开发人员必须掌握的内容。全毛涵盖了JavaScript的个钟高级、有用的特性。
> 读者笔名是`Yexk`。笔者不才由PHP后端入门，工作中慢慢的转型到了web前端。
邮箱：`yexk@yexk.cn`。欢迎大家来点评和指正。

# 第一章：JavaScript简介
讲述了JavaScript的起源，因何而生，如何发展。现状（从书的2012年的）。笔者接下来补充下2012~2017年发生的事件。设计的`BOM`、`DOM`、ECMA的想关事情和发展。

## JavaScript简史
JavaScript诞生于1995年。当时它主要目的是处理以前由服务器端语言负责一些校验工作。慢慢的发展成浏览器必备的一项特色功能。如今JavaScript的用途早已不再局限简单的验证数据了，慢慢的成为了一门功能全面的变成语言。

## 版本
JavaScript已经被Netscape公司提交给ECMA制定为标准，称之为ECMAScript，标准编号ECMA-262。目前最新版为ECMA-262 5th Edition。符合ECMA-262 3rd Edition标准的实现有： 

1. Microsoft公司的JScript.
2. Mozilla的JavaScript-C（C语言实现），现名SpiderMonkey
3. Mozilla的Rhino（Java实现）
4. Digital Mars公司的DMDScript
5. <span style="color:red"> Google公司的V8（目前v8引擎可以说是火的一塌糊涂。） </span>
6. WebKit

## `JavaScript`和`ECMAScript`
虽然 `JavaScript` 和 `ECMAScript` 这两个一直被人们用来表达相同的含义。但实际上 `ECMAScript` 只是制定了 `JavaScript`核心语言（基础）。而 `JavaScript`是由 `ECMAScript`、 `BOM` 和 `DOM` 组成。

1. `ECMAScript` ，描述了该语言的语法和基本对象。
2. `DOM` （文档对象模型），描述处理网页内容的方法和接口。 
3. `BOM` （浏览器对象模型），描述与浏览器进行交互的方法和接口。

![javascript 关系图](1-1.png)

## JavaScript实现
> 由于现在的厂商出现的很多不同版本的浏览器和支持的内核。导致的JavaScript。bom对象和dom对象支持的程度都有少许的差别。这也是前端工程师的痛。

### ECMAScript
> 目前最新的版本是es7。不过在现在的开发中es6用的都很少。只是一些 `nodejs` 相关的技术才使用了到了一些。

它规定了这门语言的下列组成部分：
1. 语法。
2. 类型
3. 语句
4. 关键字
5. 保留字
6. 操作符
7. 对象

### DOM （文档对象模型）
根据书中的描述和我的所识。主要制定了对文档的操作接口。实现了控制文档显示数据。按照我们的意愿去加载所需要的内容。  
目前dom提供了三种等级。由于市场的发展。其实很少人会注意到这些区别。毕竟这些功能对于目前市面上的浏览器来说都是已经支持的了。
1. 对文档的操作提供了 `document` 对象。
2. 对元素（标签）操作提供了 `element` 对象。
3. 对元素（标签）属性操作提供了 `attribute` 对象。
4. 对元素（标签）事件监听提供了 `event` 对象。

### BOM （浏览器对象模型）
主要实现了对浏览器的信息的获取和简单的控制：
1. 弹出新浏览器窗口的功能
2. 移动、缩放和关闭浏览器窗口的功能。
3. 提供浏览器详细信息的 `navigator` 对象。
4. 提供浏览器所加载页面的详细信息的 `location` 对象。
5. 提供用户显示器详细信息的 `screen` 对象。
6. 对 `cookie` 支持。
7. 像 `XMLHttpRequest` 和 `ActiveXObject` 对象的支持。

> 由于浏览器厂商的不一样。导致的这些对象的属性和方法有少许的不一样。

# 读后感
认识 `JavaScript` 和 `EMCAScript` 的区别认识。前者基于后者提供的语法和基础的支持构建了一门脚步本语言。
浏览器产生差异性的原因是各大浏览器想争夺这个蛋糕导致的三足鼎立的情况。导致的我们开发者的复杂程度。虽然后续的 `HTML5` 有望统一，但需要完全统一需要一定的时间。




