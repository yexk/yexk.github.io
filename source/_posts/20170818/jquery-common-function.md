---
layout: blog
title: jQuery常用的方法
date: 2017-08-18 00:35:42
categories: javascript
tags: 
- jquery
- common
- function
---

> 个人总结一些工作中必须使用和掌握的jQuery方法。

<!-- more -->

## 属性
1. `attr(name|properties|key,value|fn)` : 对元素属性的操作。（`prop()`）
```JavaScript
	$('a').attr('href'); // 获取a标签的href属性值。
	$('a').attr('href','http://yexk.cn'); // 给a标签的一个属性赋值。
	$('a').attr({'href':'http://yexk.cn','title':'Yexk'}); // 给a标签的多个属性赋值。
```

2. `removeAttr(name)` : 移除元素属性。
```JavaScript
	$('a').removeAttr('href'); // 移除一个href属性
```
3. `addClass(class|fn)` ：添加一个class（类）名。
```JavaScript
<!-- // HTML 代码: -->
<div></div>
<!-- // jQuery 代码: -->
$("div").addClass('show_div');
<!-- // 结果： -->
<div class="show_div"></div>
```
4. `removeClass([class|fn])` : 移除元素的class（类）名。
	和3使用方法相同，效果相反。
5. `html([val|fn])` : 对元素的内容进行操作。
```JavaScript
	$('div').html('<p>我是动态追加的</p>'); // 添加内容。
	$('div').html(); // 获取内容 
	$('div').html(''); // 删除内容 
```
6. `val([val|fn])` ：对元素的value值进行操作。
	使用方法和5相同。

## 选择器
1. ID 选择器
	- `#id`
2. class 选择器
	- `.class`
3. 属性选择器
	- `[attribute]`
	- `[attribute=value]` 
4. 表单选择器
	- `:input`
	- `:submit`
	- `:selected`
5. 层级选择器
	- `#id .class`
6. 混搭使用
	- `#id .class input[type="text"]`

## 筛选
1. `hasClass(class)` ：检查当前的元素是否含有某个特定的类，如果有，则返回true。
```JavaScript
<!-- // html代码 -->
<div class="show"></div>
<!-- // jQuery 代码 -->
$('div').hasClass('show'); // true;
```
2. `children([expr])` : 获取当前对象的子集（被选中的）。
```JavaScript
<!-- // html代码 -->
<ul>
	<li>1</li>
	<li class="li_ele">2</li>
	<li class="li_ele">3</li>
</ul>
<!-- // jQuery 代码 -->
$('ul').children('.li_ele'); // 获取到了第二个和第三个li元素
```
3. `find(expr|obj|ele)` : 获取当前对象的子集（被选中的）。 
	使用方式同上	
4. `parent([expr])` : 获取当前对象的父集。
	使用方式同上	
5. `prev([expr])` ：获取当前对象的前一个。
	使用方式同上	
5. `next([expr])` ：获取当前对象的后一个。
	使用方式同上	
6. `siblings([expr])` : 获取当前对象的所有同级元素。
	使用方式同上

## 事件
1. `on(events,[selector],[data],fn)` ：在选择元素上绑定一个或多个事件的事件处理函数。
```JavaScript
$('div').on('click', function(event) {
	/* Act on the event */
	console.log(this); // 打印div
}); // 给div加上点击事件。
```
2. `off(events,[selector],[fn])` ：在选择元素上移除一个或多个事件的事件处理函数。
```JavaScript
$('div').off('click'); // 去掉div的单击事件。
```
3. `trigger(type,[data])` ：在每一个匹配的元素上触发某类事件。
```JavaScript
$('form').trigger('submit'); // 触发表单提交事件。
```
4. `triggerHandler(type, [data])` ：触发指定的事件类型上所有绑定的处理函数。
	使用方法同上
> 如果你对一个focus事件执行了 .triggerHandler() ，浏览器默认动作将不会被触发，只会触发你绑定的动作。

	ps : 这个方法的行为表现与trigger类似，但有以下三个主要区别： 

	- 第一，他不会触发浏览器默认事件。
	- 第二，只触发jQuery对象集合中第一个元素的事件处理函数。
	- 第三，这个方法的返回的是事件处理函数的返回值，而不是据有可链性的jQuery对象。此外，如果最开始的jQuery对象集合为空，则这个方法返回 undefined。

## 效果
1. `show([speed,[easing],[fn]])` ：显示隐藏的匹配元素。
```JavaScript
<!-- // HTML 代码 -->
<p style="display: none;"></p>
<!-- // jQuery 代码 -->
$('p').show(); // 立即显示。如果想显示动画可以传时间进去。`$('P').show(1000)`
```
2. `hide([speed,[easing],[fn]])` ：隐藏显示的元素。
	使用方法同上
3. `animate(params,[speed],[easing],[fn])` : 用于创建自定义动画的函数。
```JavaScript
<!-- // HTML 代码: -->
<button id="run">Run</button>
<div id="ye_animate">Hello!</div>
<!-- // jQuery 代码: -->
$("#run").click(function(){
  $("#ye_animate").animate({ 
    width: "90%",
    height: "100%",
    fontSize: "10em"
  }, 1000 );
}); // 在一个动画中同时应用三种类型的效果。
```
4. `stop([clearQueue],[jumpToEnd])` ：立即停止动画效果。
```JavaScript
// 假设上面的已经点击了‘Run’。我们在创建一个stop按钮。
<!-- // HTML 代码: -->
<button id="stop"></button>
<!-- // jQuery 代码: -->
$("#stop").click(function(){
  $("#ye_animate").stop();
}); // 立即停止动画。
```

## AJAX
1. `jQuery.ajax(url,[settings])` : 创建同步或者异步的 HTTP 请求加载远程数据。
```JavaScript
$.ajax({
	url: '/path/to/file', // 请求的路径
	type: 'default GET (Other values: POST)', // 请求的类型
	dataType: 'default: Intelligent Guess (Other values: xml, json, script, or html)', // 请求头的数据类型。
	async : true , // 同步或者异步， （默认是TRUE，异步。）
	data: {param1: 'value1'}, // 请求的参数。
	beforeSend: function(){
		// 请求发送到请求返回前的时间。
	},
	success:function(data){
		// 返回成功后的处理代码。
	},
	error:function(){
		// 请求失败后。
	}
})
```
2. `jQuery.get(url, [data], [callback], [type])` : 默认是GET请求。
```JavaScript
$.get('/path/to/file', function(data) {
	// 返回成功后的处理代码	
});
```
3. `jQuery.post(url, [data], [callback], [type])` ： 默认是POST请求。
```JavaScript
$.post('/path/to/file', {param1: 'value1'}, function(data, textStatus, xhr) {
	// 返回成功后的处理代码	
});	
```
4. `jQuery.getScript(url, [callback])` ：GET 请求载入并执行一个 JavaScript 文件。
```JavaScript
$.getScript("/path/to/file", function(){
	// 返回成功后的处理代码	
});	
```

## 其他常用
1. `each(callback)` : 遍历对象。
```JavaScript
<!-- // HTML 代码: -->
<img/><img/><img/>
<!-- // jQuery 代码: -->
$("img").each(function(i){
   this.src = "test" + i + ".jpg"; // this指向调用着。（原生的dom对象）
 });
<!-- // 结果： -->
<img src="test0.jpg" /><img src="test1.jpg" /><img src="test2.jpg" />
```
2. `data([key],[value])` : 在一个div上存取数据。
```JavaScript
<!-- //	HTML 代码: -->
<div data-index="ye_cs"></div>
<!-- // jQuery 代码: -->
$("div").data("index");  // ye_cs
$("div").data("str", "hello world");  // blah设置为hello
```

3. `jQuery.each(object, [callback])` ： 遍历对象。
	使用方式同1。
4. `jQuery.type(obj)` : 检测obj的数据类型。
	- jQuery.type(true)         === "boolean"
	- jQuery.type(3)            === "number"
	- jQuery.type("test")       === "string"
	- jQuery.type(function(){}) === "function"
	- jQuery.type([])           === "array"
	- jQuery.type(new Date())   === "date"
	- jQuery.type(/test/)       === "regexp"
4. `event.preventDefault()` ：阻止默认事件行为的触发。

5. `serialize()` ：序列表表格内容为字符串。