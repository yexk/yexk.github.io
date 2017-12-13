---
layout: blog
title: JavaScript高级程序设计第三版（读后感）（第三篇）
date: 2017-12-10 20:28:09
categories: professional_javascript_for_web_develop_3rd
tags: JavaScript-web-develop-3rd
---

# JavaScript高级程序设计第三版（读后感）（第三篇）
> 在上一篇中，讲了JavaScript的使用方式（引用方式）。总得来说无非就是 `script` 标签和脚本的引用。接下来继续读第三章，这一章开始讲述了 `JavaScript` 基础语法，这个还好，`JavaScript` 是一个弱类型的语言。借鉴的 `Java` 和 `c` 等高级语言的语法。使得其他编程语言上手也不算有难度。  


## 基本语法
和众多编程一样，有 `区分大小写` 、`关键字` 、 `标识符` 等规则。但和 `Java` 、`C` 不一样的是这门语言没有那么严格的变量类型。也就意味着一个变量可以存放任何东西，这点和 `PHP` 类似，

## 标识符

- 第一个字符必须是一个`字母`、`下划线（_）`或者一个`美元符号（$）`;
- 其他字符可以是`字母`、`下划线`、`美元符号`或者`数字`。
- 标识符的字母也可以包含扩展的 `ASCII` 或 `Unicode` 字母字符。

> 按照惯例，`ECMAScript` 标识符采用`小驼峰`的命名方式。也推荐其标识符的时候使用`小驼峰`的形式。

## 数据类型（7种）
JavaScript语言可以识别下面 7 种不同类型的值：
  
六种 `原型` 数据类型:

- `Boolean` .  布尔值，`true` 和 `false`.
- `null` . 一个表明 `null` 值的特殊关键字。 `JavaScript` 是大小写敏感的，因此 `null` 与 `Null`、`NULL`或其他变量完全不同。
- `undefined` .  变量未定义时的属性。
- `Number` .  表示数字，例如： `42` 或者 `3.14159`。
- `String` .  表示字符串，例如：`"Howdy"`
- `Symbol` . ( 在 `ECMAScript 6` 中新添加的类型)。一种数据类型，它的实例是唯一且不可改变的。

以及 `Object` 对象。

## 操作符（运算符）
JavaScript 拥有如下类型的运算符。书中详细的描述了运算符和运算符的优先级。

- 赋值运算符(Assignment operators)
- 比较运算符(Comparison operators)
- 算数运算符(Arithmetic operators)
- 位运算符(Bitwise operators)
- 逻辑运算符(Logical operators)
- 字符串运算符(String operators)
- 条件（三元）运算符(Conditional operator)
- 逗号运算符(Comma operator)
- 一元运算符(Unary operators)
- 关系运算符(Relational operator)

其他的运算符合别的语言都没有很大的区别。这里笔者想提一下 `一元运算符(Unary operators)` ，这个算是 `JavaScript` 语言中比较独特的语法。书中没有提到的，笔者这里做点补充：  

### 一元运算符(Unary operators)
> 除去自增自减是一元运算符以为，JavaScript还提供了下面的几种一元运算符。

- typeof 
	> `typeof` 运算符返回一个表示 `xxx` 类型的字符串值。`xxx` 可为字符串、变量、关键词或对象，其类型将被返回。
- delete
	> `delete` 运算符, 删除一个对象或一个对象的属性或者一个数组中某一个键值。
- vold
	> `void` 运算符,表明一个运算没有返回值。	

**typeof 运算符** 
```JavaScript
typeof operand
typeof (operand)
```
`typeof` 操作符返回一个表示 `operand` 类型的字符串值。 `operand` 可为字符串、变量、关键词或对象，其类型将被返回。 `operand` 两侧的括号为可选。  
案例：  
```JavaScript
var myFun = new Function("5 + 2");
var shape = "round";
var size = 1;
var today = new Date();

typeof myFun;     // return "function"
typeof shape;     // return "string"
typeof size;      // return "number"
typeof today;     // return "object"
typeof dontExist; // return "undefined"

```
> `typeof` 常用于数据类型的判断。通过类型结果继续下一步操作。 

**delete 运算符** 
```JavaScript
delete objectName;
delete objectName.property;
delete objectName[index];
```
`objectName` 是一个对象名, `property` 是一个已经存在的属性, `index` 是数组中的一个已经存在的键值的索引值.
> 不推荐使用，并在ECMAScript中5严格模式是被禁止的。推荐的替代方案是分配要访问到一个临时变量，其属性的对象。  
>删除数组中的元素时，数组的长度是不变的，例如 delete a[3], a[4]  ，a[4] 和a[3] 仍然存在变成了undefined.

**vold 运算符**   
这个在c语言和java中都可以看到。都是代表函数声明没有返回值的时候。在JavaScript也差不多是这个情况。大家一定看过这个情况：`<a href="javascript:void(0)">click here . Yexk</a>` 这个汉代么点击的时候不会发生任何效果。

## 语句（流程控制语句）
流程控制语句是编程领域一个很重要的语法，语句通常使用一个或者多个关键字来完成指定的任务。这个很多语言上都差不多。

- if
- do-while
- while
- for 
- forin 
- label
- switch

书中的语法相对比较详细。笔者想提及一个同样用于遍历的方法 `forEach` : 对数组的每个元素执行一次提供的函数。  

**语法：**
```JavaScript
array.forEach(callback(currentValue, index, array){
    //do something
}, this)

array.forEach(callback[, thisArg])	
```
**参数**   
callback:为数组中每个元素执行的函数，该函数接收三个参数：   
currentValue(当前值):数组中正在处理的当前元素。   
index(索引):数组中正在处理的当前元素的索引。   
array:forEach()方法正在操作的数组。   
[thisArg]可选:可选参数。当执行回调 函数时用作this的值(参考对象)。   
**返回值**    
undefined.    
**支持情况**   
主流浏览器和IE9+   

```JavaScript
const arr = ['a', 'b', 'c'];
arr.forEach(function(element) {
    console.log(element);
});
arr.forEach( element => console.log(element));

// a
// b
// c	
```
## 函数
函数对任何语言来说都一个核心的概念。通过函数可以封装任意多条语句，而且可以在任何地方、任何时候调用。 `JavaScript` 中的函数使用的更多的是匿名函数，后续会有专门的章节对函数进行讲述。可以看 `第7章函数表达式` 

在 ES6 中，函数新增了一个箭头函数，所谓是为开发者提供了一个便利。简介的语法，对 this 指向的修改。对我开发者还是很有用的。目前的市场上很多框架都在使用了。
> 书中的函数在此章节也没有说的很详细。这里就简单的知道一下这个概念就行。

# 读后感
基础语法章节，考验编程的基本工扎不扎实的时候。很多开发者都是出问题了就一头雾水，包括笔者自己也一样。虽然在调试程序上有点心得，但有时候还是需要调试一段时间。
对于调试程序，笔者觉得看结果是最好的调试方法。问题出在哪里直接看控制台错误就行，对有疑问的数据或者业务逻辑有问题，多打印结果出来看看就好。一句话基本功好，都不是问题。
> 调试心得：多看控制台，多用 `console.log(data)`。