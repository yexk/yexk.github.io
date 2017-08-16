---
layout: blog
title: bower 快速入门
date: 2017-08-15 15:37:54
categories: 前端框架
tags: 
- bower
- nodejs
- 自动化工具
---

## What is bower?(什么是bower？)

Bower是一个客户端技术的软件包管理器，它可用于搜索、安装和卸载如JavaScript、HTML、CSS之类的网络资源。使用前提，需要按照node.js。并且使用npm包管理来安装bower。

命令：`npm install -g bower` 

>PS:
>- NPM：NPM是node程序包管理器。它是捆绑在nodejs的安装程序上的，所以一旦你已经安装了node，NPM也就安装好了。 
>- 这行命令是Bower的全局安装，-g 操作表示全局。 

## How to use?(怎么使用？)
命令：`bower install <packgage>`
> eg. `bower install jquery`
上述命令完成以后，你会在你刚才创建的目录下看到一个bower_components的文件夹。里面有jQuery文件。


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<script type="text/javascript" src="bower_components/jquery/jquery.min.js"></script>
</head>
<body>
<script>
	$(function(){
		alert(1);
	});
</script>
</body>
</html>
```

其他命令：
- 包搜索：`bower search jquery`
- 包信息：`bower info jquery`
- 所有包：`bower list`
- 包卸载：`bower uninstall jquery`


## bower.json文件的作用
> 有待科普

## 结语
> 表示放弃使用。