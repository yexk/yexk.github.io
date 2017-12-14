---
layout: blog
title: css基本入门
date: 2017-08-15 01:59:34
categories: css
tags: 
- css
- 快速入门
---

# CSS基本入门

**基本语法：** `选择器{属性名:值;}`

## 选择器
常用的选择器：
1. 元素选择`p{color:red}`
2. ID选择器`#ID{color:red}`
3. CLASS类选择器`.class{color:red}`
4. 后代选择器`div p{color:red}`

## 常用的样式
#### 背景
1. 背景颜色(background-color)
2. 背景颜色(background-image)
3. 背景颜色(background-position)

	> 简写形式 `body {background:#ffffff url('img_tree.png') no-repeat right top;}`

#### 文字
1. 文本颜色(color)
2. 对齐方式(text-align)
3. 文本修饰(text-decoration)
4. 字体大小(font-size)
5. 文本修饰(font-family)

#### 内外边距
1. 内边距(padding)
2. 外边距(margin)

#### 边框
1、边框


#### 定位
1. 静态定位（static）
2. 相对定位（relative）
3. 绝对定位（absolute）
4. 固定定位（fixed）

#### 浮动
1. 左浮动
2. 右浮动
3. 清除浮动

#### 伪类元素


## 引用方式
样式的引用方式:
- 外部样式表（`<link rel="stylesheet" type="text/css" href="style.css">`）
- 内部样式表（`<style>p{color:red}</style>`）
- (X)导入样式（`<style type="text/css"> @import "style.css"</style>`）
- 内联(行内)样式（`<p style="color:sienna;margin-left:20px">This is a paragraph.</p>`）

>**样式权重问题：**
>浏览器缺省设置 -> 外部样式表 -> 内部样式表（位于 <head> 标签内部） -> 内联样式（在 HTML 元素内部）。
>标签选择器 -> 类选择器 -> ID选择器 

