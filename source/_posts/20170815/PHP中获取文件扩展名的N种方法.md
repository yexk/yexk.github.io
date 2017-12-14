---
layout: blog
title: PHP中获取文件扩展名的N种方法
date: 2017-08-15 01:48:26
categories: php 
tags: 
- php
- function 
---

## PHP中获取文件扩展名的N种方法 
从网上收罗的，基本上就以下这几种方式：
  
#### 第1种方法：
```php
<?php
function get_extension($file)
{
	return substr(strrchr($file, '.'), 1);
}
```
#### 第2种方法：
```php
<?php
function get_extension($file)
{
	return substr($file, strrpos($file, '.')+1);
}
```
#### 第3种方法：
```php
<?php
function get_extension($file)
{
	$info = explode('.', $file);
	return end($info);
}
```
#### 第4种方法：
```php
<?php
function get_extension($file)
{
	$info = pathinfo($file);
	return $info['extension'];
}
```
#### 第5种方法：
```php
<?php
function get_extension($file)
{
	return pathinfo($file, PATHINFO_EXTENSION);
}
```
> 大概看了下上面的几种情况。你会喜欢用几种呢？

接下来就开始测试一下各种刁钻的问题。

- 路径1. /home/test  
- 路径2. /init.d/test  
- 路径3. test.tar.gz  

对应这四个情况。发现使用路径1去测试方法4，出现警告：`Undefined index: extension`。    
使用路径2去测试方法1,方法2,方法3，都出现了取错后缀的问题。    
方法5基本能应对上面的路径1和路径2。但还有一个问题。那就是遇到tar.gz这样的后缀的时候还是会有问题。  
所以路径3的后缀是tar.gz，使用以上几种的方式都不能正确的取得后缀名，这个还是需要自己写一个判断或者限定。
