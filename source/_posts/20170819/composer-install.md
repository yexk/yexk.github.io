---
layout: blog
title: composer安装和使用
date: 2017-08-19 13:51:08
categories: composer
tags:
- composer
---

> Composer 是 PHP 的一个依赖管理工具。它允许你申明项目所依赖的代码库，它会在你的项目中为你安装他们。

<!-- more -->

## 下载和安装

**composer的用途**：
a) 你有一个项目依赖于若干个库。
b) 其中一些库依赖于其他库。
c) 你声明你所依赖的东西。
d) Composer 会找出哪个版本的包需要安装，并安装它们（将它们下载到你的项目中）。

## Linux安装
下载 Composer 的可执行文件

### 局部安装
>要真正获取 Composer，我们需要做两件事。首先安装 Composer （同样的，这意味着它将下载到你的项目中）：  

```
curl -sS https://getcomposer.org/installer | php
```

> 注意： 如果上述方法由于某些原因失败了，你还可以通过 php >下载安装器：
`php -r "readfile('https://getcomposer.org/installer');" | php`   

你可以通过 --install-dir 选项指定 Composer 的安装目录（它可以是一个绝对或相对路径）：
```
curl -sS https://getcomposer.org/installer | php -- --install-dir=bin
```

### 全局安装(推荐)
你可以将此文件放在任何地方。如果你把它放在系统的 PATH 目录中，你就能在全局访问它。 在类Unix系统中，你甚至可以在使用时不加 php 前缀。

你可以执行这些命令让 composer 在你的系统中进行全局调用：
```
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
```
>注意： 如果上诉命令因为权限执行失败， 请使用 sudo 再次尝试运行 mv 那行命令。

现在只需要运行 composer 命令就可以使用 Composer 而不需要输入 php composer.phar。

## Windows安装
使用安装程序 [Composer-Setup.exe](http://pan.baidu.com/s/1i5qVZud) 附上下载链接：http://pan.baidu.com/s/1i5qVZud

这是将 Composer 安装在你机器上的最简单的方法。

下载并且运行 [`Composer-Setup.exe`](http://pan.baidu.com/s/1i5qVZud)，它将安装最新版本的 Composer ，并设置好系统的环境变量，因此你可以在任何目录下直接使用 `composer` 命令。

**<span style="color:red">注意：win10电脑必须用管理员权限安装！！！</span>**

---
> 由于改软件的服务器在国外。国内的速度。。。你懂的。。这里我们需要改成中国的镜像。

## 镜像用法

有两种方式启用本镜像服务：

- **系统全局配置**： 即将配置信息添加到 Composer 的全局配置文件 config.json 中。见“方法一”
- **单个项目配置**： 将配置信息添加到某个项目的 composer.json 文件中。见“方法二”

### 方法一： 修改 composer 的全局配置文件（推荐方式）

打开命令行窗口（windows用户）或控制台（Linux、Mac 用户）并执行如下命令：

```
composer config -g repo.packagist composer https://packagist.phpcomposer.com
```

### 方法二： 修改当前项目的 composer.json 配置文件：

打开命令行窗口（windows用户）或控制台（Linux、Mac 用户），进入你的项目的根目录（也就是 composer.json 文件所在目录），执行如下命令：

```
composer config repo.packagist composer https://packagist.phpcomposer.com
```

上述命令将会在当前项目中的 composer.json 文件的末尾自动添加镜像的配置信息（你也可以自己手工添加）：

```
"repositories": {
    "packagist": {
        "type": "composer",
        "url": "https://packagist.phpcomposer.com"
    }
}
```

以 laravel 项目的 composer.json 配置文件为例，执行上述命令后如下所示（注意最后几行）：

```
{
    "name": "laravel/laravel",
    "description": "The Laravel Framework.",
    "keywords": ["framework", "laravel"],
    "license": "MIT",
    "type": "project",
    "require": {
        "php": ">=5.5.9",
        "laravel/framework": "5.2.*"
    },
    "config": {
        "preferred-install": "dist"
    },
    "repositories": {
        "packagist": {
            "type": "composer",
            "url": "https://packagist.phpcomposer.com"
        }
    }
}
```

OK，一切搞定！试一下 composer install 来体验飞一般的速度吧！

查看修改成功了没有？
```shell
修改前
# composer config -g -l
[repositories.packagist.org.type] composer
[repositories.packagist.org.url] https?://packagist.org

修改后
# composer config -g -l
[repositories.packagist.org.type] composer
[repositories.packagist.org.url] https://packagist.phpcomposer.com
```

这样就代表修改成功咯！！
