---
layout: blog
title: 联想air13的触摸板双指右键失效的问题
date: 2018-05-03 18:49:03
categories: lenovo
tags: lenovo
---

1. 打开注册表 `Win+R` , 输入 `regedit` 回车
2. 在注册表找到如下路径
```
注册表路径：计算机\HKEY_CURRENT_USER\Software\Elantech\SmartPad
```
3. 改如下两个值：
```
Tap_Two_Finger
Tap_Two_Finger_Enable 
```
把这两个值都改成1，原来是7,0
4. 重启电脑

结果图：
![20170730004052.png](20170730004052.png)

