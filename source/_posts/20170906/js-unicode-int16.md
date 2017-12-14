---
layout: blog
title: JavaScript unicode和16进制互转
date: 2017-09-06 20:51:17
categories: javascript
tags: 
---

> 有时候会遇到一些问题。传入后台的数据如果是中文的就识别不了，比如后台对中文支持的不是很好的话。就可以使用这套函数转换一下。

<!-- more -->

```JavaScript
/**
 * Unicode字符串转16进制
 * eg: 
 *  unicodetoInt16('Yexk_M 极致分享 ym125.cc') 
 *  //输出：0x5965786B5F4D20E69E81E887B4E58886E4BAAB20796D3132352E6363
 * @Author   Yexk       <yexk@yexk.cn>
 * @DateTime 2017-09-06
 * @param    {[string]}   str                [字符串]
 * @return   {[int]}                         [16进制数]
 */
function unicodetoInt16(str)
{
	str = str.split('');
	for (var i = 0; i < str.length; i++) {
		if (str[i].charCodeAt(0)>255) {
			str[i] = encodeURI(str[i]);
			str[i] = str[i].replace(/%/ig,'');
		}else{
			str[i] = str[i].charCodeAt(0).toString(16);
		}
	}
　　return '0x'+(str.join("")).toUpperCase();
}

/**
 * 传入十六进制数进行中文解码。
 * eg:
 *  int16toUnicode('0x5965786B5F4D20E69E81E887B4E58886E4BAAB20796D3132352E6363') 
 *  //输出：Yexk_M 极致分享 ym125.cc
 * @Author   Yexk       <yexk@yexk.cn>
 * @DateTime 2017-09-06
 * @param    {[int]}   int             [传入16进制数]
 * @return   {[string]}                [返回解码后的字符串]
 */
function int16toUnicode(int16)
{
	var tmp='';
	int16 = int16.substring(2);
	if (int16.length % 2) return '';
	for(var iii = 0; iii < int16.length; iii += 2)
	{
		tmp += '%' + int16.charAt(iii) + int16.charAt(iii+1);
	}
	return decodeURI(tmp);
}

```
