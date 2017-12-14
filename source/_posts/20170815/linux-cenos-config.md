---
layout: blog
title: Linux centos 配置更新yum源
date: 2017-08-15 16:33:56
categories: linux
tags:
- centos
- centos 7
- linux
---

在CentOS 7下更改yum源与更新系统。

[1] 首先备份/etc/yum.repos.d/CentOS-Base.repo
```shell
cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```
<!-- more -->

[2] 进入yum源配置文件所在文件夹
```
[root@localhost yum.repos.d]# cd /etc/yum.repos.d/
```
[3] 下载163的yum源配置文件，放入/etc/yum.repos.d/(操作前请做好相应备份)
```
[root@localhost yum.repos.d]# wget http://mirrors.163.com/.help/CentOS6-Base-163.repo
```
[4] 运行yum makecache生成缓存
```
[root@localhost yum.repos.d]# yum makecache
```
[5] 更新系统(时间比较久,主要看个人网速)
```
[root@localhost yum.repos.d]# yum -y update
```
> 到这一步就可以更新完成了。


# 一、查看SELinux状态命令：
1、/usr/sbin/sestatus -v      ##如果SELinux status参数为enabled即为开启状态
SELinux status:                 enabled
2、getenforce                 ##也可以用这个命令检查

# 二、关闭SELinux方法：
1、临时关闭（不用重启机器）：

复制代码代码如下:
```
setenforce 0 #设置SELinux 成为permissive模式
#setenforce 1 设置SELinux 成为enforcing模式
```
2、修改配置文件需要重启机器：
修改/etc/selinux/config 文件
将SELINUX=enforcing改为SELINUX=disabled
重启机器即可
