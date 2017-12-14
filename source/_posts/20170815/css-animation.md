---
layout: blog
title: 动画效果 (Animation)
date: 2017-08-15 16:27:49
categories: css
tags:
- animation
- css动画
---

# 动画效果 (Animation)
> 定义一写自己喜欢的动画效果。通过 CSS3，我们能够创建动画，这可以在许多网页中取代动画图片、Flash 动画以及 JavaScript。

## 定义
animation 属性是一个简写属性，用于设置六个动画属性：    
animation-name （动画名称）   
animation-duration （时间）   
animation-timing-function （速度曲线）   
animation-delay （延时）   
animation-iteration-count （播放的次数）   
animation-direction （反向播放）    

<!-- more -->

| 值 | 描述 |
| -- | --   |
| animation-name | 	规定需要绑定到选择器的 keyframe 名称。。|
| animation-duration | 	规定完成动画所花费的时间，以秒或毫秒计。|
| animation-timing-function | 	规定动画的速度曲线。|
| animation-delay | 	规定在动画开始之前的延迟。|
| animation-iteration-count | 	规定动画应该播放的次数。|
| animation-direction | 	规定是否应该轮流反向播放动画。| 
  
## 语法
`animation: name duration timing-function delay iteration-count direction;`   

| 属性 | name | duration | timing-function | delay | iteration-count | direction |
| --------- | ---- | -------- | --------------- | ----- | --------------- | --------- |
| 值 | keyframename | time | linear | time  | n | normal |
|    | none |  | ease |  | infinite | alternate |
|    |      |  | ease-in |  | | |
|    |      |  | ease-out  |  | | |
|    |      |  | ease-in-out  |  | | |
|    |      |  | ease-in-out  |  | | |
|    |      |  | cubic-bezier(n,n,n,n) |  | | |

**简单案例**：    
css >>>
```css
.circle{
	width: 100px;
	height: 100px;
	border-radius: 50%;
	line-height: 100px;
	text-align: center;
	background-color: #ccc;
}
.circle:hover{
	/* animation */
	animation: circle 1s linear infinite alternate;
}
@keyframes circle {
	from { box-shadow: 0px 0px 1px #00A4C1; }
	to { box-shadow: 0px 0px 20px #00A4C1; }
}
```
html >>>
```JavaScript
<div class="circle">Yexk</div>
```
{% asset_img 1_css_animate.gif %}

### 1. name
为 @keyframes 动画规定名称。   
**语法：** `animation-name: keyframename|none;`    

| 值 | 描述 |
| -- | -- |
| keyframename | 规定需要绑定到选择器的 keyframe 的名称。|
| none | 规定无动画效果（可用于覆盖来自级联的动画）。|

### 2. duration
定义动画完成一个周期所需要的时间，以秒或毫秒计。
**语法：** `animation-duration: time;`

| 值 | 描述 |
| -- | -- |
|time | 规定完成动画所花费的时间。默认值是 0，意味着没有动画效果。|

### 3. timing-function
定义动画的速度曲线。速度曲线定义动画从一套 CSS 样式变为另一套所用的时间。   
**语法：** `animation-timing-function: value;`

| 值 | 描述 |
| -- | -- |
| linear | 动画从头到尾的速度是相同的。|
| ease | 默认。动画以低速开始，然后加快，在结束前变慢。|
| ease-in | 动画以低速开始。|
| ease-out | 动画以低速结束。|
| ease-in-out | 动画以低速开始和结束。|
| cubic-bezier(n,n,n,n) | 在 cubic-bezier 函数中自己的值。可能的值是从 0 到 1 的数值。|

### 4. delay
定义动画何时开始。    
**语法：** `animation-timing-function: value;`  


| 值 | 描述 |
| -- | ---- |
| time | 可选。定义动画开始前等待的时间，以秒或毫秒计。默认值是 0。 |

### 5. iteration-count
定义动画的播放次数。
**语法：** `animation-iteration-count: n|infinite;`   


| 值 | 描述 |
| -- | ---- |
| n | 定义动画播放次数的数值。 |
| infinite | 规定动画应该无限次播放。 |


### 6. direction
定义是否应该轮流反向播放动画。如果 animation-direction 值是 "alternate"，则动画会在奇数次数（1、3、5 等等）正常播放，而在偶数次数（2、4、6 等等）向后播放。  

**语法** `animation-direction: normal|alternate;`

| 值 | 描述 |
| -- | ---- |
| normal | 默认值。动画应该正常播放。 |
| alternate | 动画应该轮流反向播放。 |


__实战运用：__

参考 animate.css