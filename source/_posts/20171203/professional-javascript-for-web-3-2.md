---
layout: blog
title: JavaScript高级程序设计第三版（读后感）（第二篇）
date: 2017-12-03 10:55:46
categories: professional_javascript_for_web_develop_3rd
tags: JavaScript-web-develop-3rd
---
# JavaScript高级程序设计第三版（读后感）（第二篇）
> 在上一篇中。我们提到了JavaScript的简史。在这一篇中简单的说说这本书的第二章。

在书中的第二章中分为5个小节。分别介绍了 `JavaScript` 的简单使用、应用。脚本的几种使用方式。文档模式对脚本的影响。

## `script` 元素
书中提到的是 html4.01 中 html有6个属性。分别是：

| 属性 | 值 | 描述 |
| -- | -- | -- |
| type | MIME-type | 指示脚本的 MIME 类型。 |
| async | async | 规定异步执行脚本（仅适用于外部脚本）。 |
| charset | charset | 规定在外部脚本文件中使用的字符编码。 |
| defer | defer | 规定是否对脚本执行进行延迟，直到页面加载为止。 |
| language | script | 不赞成使用。规定脚本语言。请使用 type 属性代替它。 |
| src | URL | 规定外部脚本文件的 URL。 |

但实际上现在大多数页面上用的只有两种：
```JavaScript
	// 第一种：
	<script src="URL"></script>
	// 第二种：
	<script src="URL" type="MIME"></script>
	// MIME : `text/javascript`, `text/ecmascript`, `application/javascript` 和 `application/ecmascript`, `text/x-template` ...
```
## 嵌入代码与外部文件
在html中写JavaScript在正常不过了。但现在的js动不动就是上千上万行。那维护成本。。。难以想象。  
也就是现在常用了两种写JavaScript的方式：
```JavaScript
	// 1、 外部文件
	<script src="URL"></script>
	// 2、 嵌入代码
	<script>
		// javascript 代码
	</script>
```

工作中会出现一些争议，`script` 标签是放到哪里才比较好呢？但是在手册中（文档）都会告诉我们应该放到 `head` 标签里面。但业界比较好的做法是放到 `body` 标签的最后一行。如：
```JavaScript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
	<script src="URL"></script>
	<script>
		// javascript 代码
	</script>
</body>
</html>
```
## `noscript` 元素
> 实际工作中也很少用到。笔者自己也很少写。可能是我的工作中比较少遇到吧。

这个标签主要对于早期的浏览器对 `JavaScript` 的支持程度的问题做的一个兼容操作。比如浏览器不支持脚本，或者脚本被禁用。使用这个标签就可以起到提示的作用。如：
```JavaScript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	<noscript>
		<h1>本页面需要浏览器的支持。请启用浏览器，或者更换浏览器。</h1>
	</noscript>
</body>
</html>
```
> 以现在的情况。已经不存在浏览器不支持js的情况了。所以这个标签后续的作用会慢慢的淡化。以至于很少有人会用到。

# 读后感
- `JavaScript` 插入到 `html` 需要使用 `script` 标签。
- 引用方式有两种：嵌入代码和外部文件。

不知道现在学前端的同学有没有发现。。。其实前端 `自动化后`，`工程化后`，这些关系已经不是很明显了。所有的代码被拆分的零零散散。若老一辈前端程序员（也就是使用Dreamweaver开发的），如果他们再去做页面估计他们会崩溃的。
