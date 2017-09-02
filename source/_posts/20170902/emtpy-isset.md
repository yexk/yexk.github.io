---
layout: blog
title: ISSET和EMPTY的区别
date: 2017-09-02 20:12:16
categories: PHP
tags:
- isset
- empty
---

isset 和 empty 这两个东西一直困扰则我。。判断的时候到底用什么好呢？

<!-- more -->

### empty：检查一个变量是否为空
empty 使用变量和null判断。如果等于就返回true，否则返回true。
	
### isset：检查变量是否设置
isset 判断变量是否已定义，同时判断变量是否赋值，并且赋值不能为null。满足以上条件就返回true，否则返回false 。

![code.png](code.png)

### 总结：
其实`empty`（判断变量是否为空）和 `isset`（判断变量是否设置）  
总体来说出去一些特殊的字符:
	- ""（空字符串不带空格），
	- "  "（空字符串带空格） , 
	- 0 , "0"（字符串零） , 
	- null , 
	- $var(定义未赋值) , 
	- array()（空数组）， 
	- false 
这些值是特注意的。  
**还有一种情况要特别注意**：  
当变量为空字符的时候又分为**有**空格和**无**空格的。
<span style="color:red">当使用`empty`判断空字符串**有空格（$x = "  "）**的时候，返回false。</span>
<span style="color:red">当使用`empty`判断空字符**无空格（$x = ""）**的时候，返回true。</span>
<span style="color:red">**同时要注意empty和isset是判断变量的，不能直接判断值。**</span>


---
### 最后附上官方的对比图
![php_isset_empty.png](php_isset_empty.png)