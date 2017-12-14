---
layout: blog
title: git命令行秘钥创建
date: 2017-08-15 01:46:01
categories: git
tags: github
---

1. 打开 `Git Bash.` 命令行。
2. 输入命令
```
ssh-keygen -t rsa -C "your_email@example.com"
```
	> 将邮箱换成你的邮箱，一直按回车就好了。

3. 最后会在用户目录下生成 `~/.ssh/id_rsa` 和 `~/.ssh/id_rsa.pub` 文件

4. 在GitHub页面上的个人设置里面找到`SSH and GPG keys`
然后点击 `New SSH key` 
把刚刚创建的 `id_rsa.pub` 文件的内容添加到里面去。保存。

5. 最终大工搞成。