---
typora-copy-images-to: images
typora-root-url: images
---

# css笔记

## 设置css基础样式

### reset.css

```css
body {margin: 0;font:12px font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;background: #fff;}
h1,h2,h3,h4,h5,h6,p {margin: 0;}
ul,ol,dl,dt,dd {margin: 0;padding:0;}
li {list-style: none;}
a {text-decoration: none;}
img {display: inline-block; border: none;}
input,button{ margin:0; padding:0; outline: none;}
i {font-style: normal;}
```

### common.css

```css
.clearfix:after {content: "";display: block;clear: both;visibility: hidden;height: 0;}
.clearfix {zoom: 1;}
.fl {float: left;}
.fr {float: right;}
```

### mixin.scss

```css
@mixin bottom-1px($color) {
  position: relative;
  &:after {
    display: block;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    border-top: 1px solid $color;
    content: '';
  }
}

@mixin border-none() {
  &:after {
    display: none;
  }
}

@mixin elliptical() {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

## 基础知识、概念

### 引入css文件的4种方法

    1.外部样式表:外部引入法link
    2.导入法:一个css文件导入到另一个css文件@import url();
    3.嵌入样式表：嵌入法 （在head标签对中写style标签对）
    4.行内样式表:style属性

### 属性选择器

```css
/* 属性选择器：(和后台结合，比如操作表单) */

E[attr]: 选中E元素并且有attr这个属性  div[class]

E[attr="box"]:选中E元素并且有attr属性，并且属性值是box;

div[class="box"]

E[attr|="box"]: 匹配E元素，attr属性值中有连字符，以box单词开头（它本身也会被选中）

E[attr~="box"]: 匹配E元素，attr属性值中有空格，并且其中一个单词是box(它本身也会被选中)

E[attr*="box"]: 匹配E元素，attr属性值包含字母box的元素会被选中(字母连续)

E[attr^="b"]: 匹配E元素，attr属性值中以b开头的元素会被选中

E[attr$="b"]: 匹配E元素，attr属性值中以b结尾的元素会被选中
```


### 帧窗口技术

```html
<--
帧窗口技术：
页面分成不同的窗口，各个窗口之间有联系并且可以进行相互操作
-->

<frameset rows="20%,80%" frameborder="1" border="10" bordercolor="red">	
	<frame src="aa.html" name="top">
	<frameset cols="20%,80%" frameborder="1" border="10" bordercolor="red">	
		<!-- noresize 禁止拖动			 -->
		<frame noresize="noresize" src="bb1.html" name="left">
		<frame src="bb2.html" name="right">
	</frameset>
</frameset>

<!-- noframes  当浏览器不支持noframes时提示 -->
<noframes>
	您的浏览器不支持框架，请用最新的浏览器浏览页面
</noframes>

```


```html
<style>
		#fra1 {
			width: 100%;
			height: 200px;
			border-bottom: 5px solid red;
		}
		#fra2 {
			width: 30%;
			min-height: 600px;
			border-right: 5px solid red;
		}
		#fra3 {
			width: 65%;
			min-height: 600px;
		}
	</style>

<body>	
	<!-- iframe帧窗口技术
	可以和body共存
	src页面路径   name属性作用：  名称  引用 -->

	<iframe src="aa.html" frameborder="1" id="fra1" name="top"></iframe>
	<iframe src="bb1.html" frameborder="1" id="fra2" name="left"></iframe>
	<iframe src="bb2.html" frameborder="1" id="fra3" name="right"></iframe>
</body>
```







### display、visibility、overflow、opcity的区别

##### 1.display: none;

```
整个元素的显示状态是不可见的，浏览器会认为这个元素不存在
```

##### 2.visibility: hidden;

```
浏览器会认为该元素存在，但是显示不出来，该隐藏的元素还是会占据原有的位置
```

##### 3.overflow: hidden;

```
只是对超出容器内容进行处理
```

##### 4.opcity:0;

```html
浏览器会认为该元素存在，但是显示不出来，该隐藏的元素还是会占据原有的位置opcity同visibility一样，0隐藏，1显示
```

### 响应式页面设计

```css
/*设备  屏幕                 阈值*/
@media screen and (min-width: 1024px) {}
@media screen and (max-width: 1024px) {}
@media screen and (min-width: 768px) and (max-width: 1024px) {}
@media screen and (max-width: 768px) {}
```

### 栅格系统

> 更快捷的实现响应式
>
> **预定义类**    css
>
> 把屏幕平均分成12列
>
> 三种终端  四种屏幕大小   移动端优先

|           | 手机 < 768px | 平板 768~992 | pc小屏 992~1200 | pc大屏 > 1200 |
| --------- | ------------ | ------------ | --------------- | ------------- |
| container | none         | 750px        | 970px           | 1170px        |
| 前缀      | col-xs-      | col-sm-      | col-md-         | col-lg-       |
| 隐藏      | hidden-xs    | hidden-sm    | hidden-md       | hidden-md     |
| 向左      | col-xs-pull- | col-sm-pull- | col-md-pull-    | col-lg-pull-  |
| 向右      | col-xs-push- | col-sm-push- | col-md-push-    | col-lg-push-  |

```css
/*
container		固定宽度
container-fluid		宽度为100%
row		行   
col		列  
pull  right
push  left 
*/
.container,
.container-fluid {
	height: auto;
	overflow: hidden;
	margin-left: auto;
	margin-right: auto;
	padding-left: 15px;
	padding-right: 15px;
	box-sizing: border-box;
}
.row {
	height: auto;
	overflow: hidden;
/*	margin-left: -15px;
	margin-right: -15px;*/     /*根据实际需要来用*/
	box-sizing: border-box;
}
.row::before,
.row::after {
	content: "";
	display: block;
	width: 0;
	height: 0;
	line-height: 0;
	clear: both;
}
[class*="col-"] {
	float: left;
	padding-left: 15px;
	padding-right: 15px;
	box-sizing: border-box;
}
@media screen and (max-width: 768px) {
	.col-xs-1 {
		width: 8.3333333%;
	}
	.col-xs-2 {
		width: 16.6666666%;
	}
	.col-xs-3 {
		width: 25%;
	}
	.col-xs-4 {
		width: 33.3333333%;
	}
	.col-xs-5 {
		width: 41.66666666%;
	}
	.col-xs-6 {
		width: 50%;
	}
	.col-xs-7 {
		width: 58.33333333%;
	}
	.col-xs-8 {
		width: 66.66666666%;
	}
	.col-xs-9 {
		width: 75%;
	}
	.col-xs-10 {
		width: 83.33333333%;
	}
	.col-xs-11 {
		width: 91.6666666%;
	}
	.col-xs-12 {
		width: 100%;
	}
}
@media screen and (min-width: 768px) and (max-width: 992px) {
	.container {
		width: 750px;
	}
	.col-sm-1 {
		width: 8.3333333%;
	}
	.col-sm-2 {
		width: 16.6666666%;
	}
	.col-sm-3 {
		width: 25%;
	}
	.col-sm-4 {
		width: 33.3333333%;
	}
	.col-sm-5 {
		width: 41.66666666%;
	}
	.col-sm-6 {
		width: 50%;
	}
	.col-sm-7 {
		width: 58.33333333%;
	}
	.col-sm-8 {
		width: 66.66666666%;
	}
	.col-sm-9 {
		width: 75%;
	}
	.col-sm-10 {
		width: 83.33333333%;
	}
	.col-sm-11 {
		width: 91.6666666%;
	}
	.col-sm-12 {
		width: 100%;
	}
}
@media screen and (min-width: 992px) and (max-width: 1200px) {
	.container {
		width: 970px;
	}
	.col-md-1 {
		width: 8.3333333%;
	}
	.col-md-2 {
		width: 16.6666666%;
	}
	.col-md-3 {
		width: 25%;
	}
	.col-md-4 {
		width: 33.3333333%;
	}
	.col-md-5 {
		width: 41.66666666%;
	}
	.col-md-6 {
		width: 50%;
	}
	.col-md-7 {
		width: 58.33333333%;
	}
	.col-md-8 {
		width: 66.66666666%;
	}
	.col-md-9 {
		width: 75%;
	}
	.col-md-10 {
		width: 83.33333333%;
	}
	.col-md-11 {
		width: 91.6666666%;
	}
	.col-md-12 {
		width: 100%;
	}
}
@media screen and (min-width: 1200px) {
	.container {
		width: 1170px;
	}
	.col-lg-1 {
		width: 8.3333333%;
	}
	.col-lg-2 {
		width: 16.6666666%;
	}
	.col-lg-3 {
		width: 25%;
	}
	.col-lg-4 {
		width: 33.3333333%;
	}
	.col-lg-5 {
		width: 41.66666666%;
	}
	.col-lg-6 {
		width: 50%;
	}
	.col-lg-7 {
		width: 58.33333333%;
	}
	.col-lg-8 {
		width: 66.66666666%;
	}
	.col-lg-9 {
		width: 75%;
	}
	.col-lg-10 {
		width: 83.33333333%;
	}
	.col-lg-11 {
		width: 91.6666666%;
	}
	.col-lg-12 {
		width: 100%;
	}
}
	.portfolio_container {
		position: relative;
		height: 842px;
		margin-bottom: -30px;
	}
	.grid-item {
		margin-bottom: 30px;
	}
	.item1 {
		position: absolute;
		left: 0;
		top: 0;
		height: 361px;
	}
	.item2 {
		position: absolute;
		left: 323px;
		top: 0;
		height: 293px;
	}
	.item3 {
		position: absolute;
		left: 646px;
		top: 0;
		height: 384px;
	}
	.item4 {
		position: absolute;
		left: 0;
		top: 391px;
		height: 276px;
	}
	.item5 {
		position: absolute;
		left: 323px;
		top: 323px;
		height: 342px;
	}
	.item6 {
		position: absolute;
		left: 646px;
		top: 414px;
		height: 249px;
	}
	.work-item {
		width: 293.33px;
		height: 100%;
	}
	.work-item img {
		display: block;
		height: 100%;
	    width: 100%;
	}
```

### 动画属性：animation

> 1. 定义动画
> 2. 绑定到选择器上
> 3. 设置属性值

#### 1、定义动画

```css
@keyframes 动画名称 {
  0% {}
  100% {}
}

@keyframes 动画名称 {
	from {
		width: 200px;
	}
	to {
		width: 500px;
	}
}
```
#### 2、绑定到选择器上


```css
/*动画名称  时间   次数*/
animation: bianse 2s 3;
```

#### 3、设置属性值

```css
	animation: bianse 2s ease 2 infinite alternate forwards;

	animation-name:									 	动画名称
	animation-duration：							  持续时间
	animation-timing-function： 				 运动方式（贝塞尔曲线）
  animation-delay：									动画延迟
  animation-iteration-count：				 运动次数  1 2 infinite（无数次）
  animation-direction：							 运动方向  normal（默认） alternate（下一次反向）
  animation-fill-mode：						   动画停止时的状态  forwards（最后状态）
  animation-play-state： 						 运动状态 running（运动） paused暂停
```

## 常用技巧

### 移动端布局常见问题

> ```html
> <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
> <meta http-equiv="X-UA-Compatible" content="ie=edge">
> ```

#### 1 横竖屏限制问题    

```html
  <meta name="x5-orientation" content="portrait | landscape" />
```
> 只支持x5内核，指的是强制进行横屏或竖屏，`portrait`是竖屏，`landscape`是横屏。

```html
  <meta name="screen-orientation" content="portrait">
```
> 只支持uc浏览器，指UC浏览器强制竖屏。

#### 2 全屏限制问题  
```html
  <meta name="x5-fullscreen" content="true" />  
```
>只支持x5内核，只QQ应用模式，强制全屏。

```html
  <meta name="full-screen" content="yes">
```
>只支持uc浏览器，指UC强制全屏。

#### 3 禁止识别电话号码和邮箱
```html
  <meta name="format-detection" content="telephone=no, email=no" />
```
> 禁止识别后，页面当中所有的邮箱和电话将不会被识别,如果有特殊需求,要配合一下代码实现

```html
  <a href="tel:110">请拨打电话110</a>
  <a href="mailto:qq@.com">请发送邮件qq@.com</a>        
```

#### 4 消除链接、表单、按钮默认背景

```css
.box{
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
```

>对表单、链接、按钮的默认背景设置成全透明，从而进行该样式的消除。

#### 5 消除按钮圆角

```css
.box{
  -webkit-appearance: none;
}
```

>在应用开发中，经常会遇到ios端和安卓端的样式显示不一样，例如同一按钮(样式一样)会显示不一样的颜色，导致项目整体的搭配不是很好。利用`-webkit-appearance: none`，就可以去除浏览器默认样式。
>

#### 6 移动端字体

* ios系统  
    + 默认中文字体是Heiti SC   
    + 默认英文字体是Helvetica   
    + 默认数字字体是HelveticaNeue   
    + 无微软雅黑字体   
* android 系统
    + 默认中文字体是Droidsansfallback  
    + 默认英文和数字字体是Droid Sans  
    + 无微软雅黑字体  
* winphone 系统
    + 默认中文字体是Dengxian(方正等线体)  
    + 默认英文和数字字体是Segoe  
    + 无微软雅黑字体     
* 结论  
    + 各个手机系统有自己的默认字体，且都不支持微软雅黑  
    + 如无特殊需求，手机端无需定义中文字体，使用系统默认  
    + 英文字体和数字字体可使用 Helvetica ，三种系统都支持    

```css
  body{
    font-family:Helvetica;
  }
```

#### 7 禁止用户设置字体大小

```css
.box{
  -webkit-text-size-adjust:100%
}
```
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
```
>解决手机横屏时默认文字会放大的问题。当`text-size-adjust` 设为 `none` 或者 `100%` 时，则关闭字体大小自动调整功能。

#### 8 禁止文字选中

```css
.box{
  -webkit-user-select:none  /*安卓不支持*/
}
```
安卓上通过以下javascript代码解决：   
```javascript
document.addEventListener("touchstart",function(e){e.preventDefault})
```
>当你不希望用户在你的网站上选择文本时，一种方法是利用js来实现，另一中方法是将`-webkit-user-select` 和`-moz-user-select` 的值设为`none`。
>请谨慎使用这个属性：因为大部分用户是来查看信息的，他们可以复制并存储下来以备将来之用，所以这种方法既无用也无效。如果你禁用了复制粘贴功能，用户还是可以通过查看源文件来获取到他们想要的内容。
>

#### 9 字体增强 font boosting

>移动端设备为了使用户能看清楚大批量的字体，会自动对字体进行放，但是只要指定了容器的高度，就能解决。

```css
  p{
    max-height:9999999px;
  }
```

#### 10 调用原生滚动事件

```css
.box{
  -webkit-overflow-scrolling:touch
}
```

>使用具有回弹效果的滚动，当手指从触摸屏上移开，内容会继续保持一段时间的滚动效果。继续滚动的速度和持续的时间和滚动手势的强烈程度成正比。
>
>该属性的值也可以为`auto`，表示使用普通滚动，当手指从触摸屏上移开，滚动会立即停止。

#### 11 CSS动画页面闪白,动画卡顿

>  解决方法:
* 尽可能地使用合成属性transform和opacity来设计CSS3动画，不使用position的left和top来定位
* 使用 CSS3 动画的时尽量利用3D加速，从而使得动画变得流畅。动画过程中的动画闪白可以通过 backface-visibility 隐藏

```css
.box{
  -webkit-transform: translate3d(0, 0, 0);
  transform: translate3d(0, 0, 0);
}
```
#### 12 fixed定位缺陷
* ios下fixed元素容易定位出错，软键盘弹出时，影响fixed元素定位
* android下fixed表现要比iOS更好，软键盘弹出时，不会影响fixed元素定位
* ios4下不支持position:fixed

>解决方案： 可用iScroll.js插件解决这个问题  

#### 13 阻止旋转屏幕时自动调整字体大小
```css
  html, body, form, fieldset, p, div, h1, h2, h3, h4, h5, h6 {
    -webkit-text-size-adjust:none;
  }
```
>当`text-size-adjust` 设为 `none` 或者 `100%` 时，则关闭字体大小自动调整功能。

#### 14 上下拉动滚动条时卡顿、慢

```css
body {
  -webkit-overflow-scrolling:touch; overflow-scrolling: touch;
}
```
> Android3+和iOS5+支持CSS3的新属性为overflow-scrolling

#### 15 禁止复制、选中文本

```css
.box{
  -webkit-user-select:none;user-select:none;
}
```
> 解决移动设备可选中页面文本(视产品需要而定)

#### 16 ios和android下触摸元素时出现半透明灰色遮罩
```css
.box{
  -webkit-tap-highlight-color:rgba(255,255,255,0)
}
```
>设置alpha值为0就可以去除半透明灰色遮罩，备注：transparent的属性值在android下无效。

#### 17 关于 iOS 与 OS X 端字体的优化(横竖屏会出现字体加粗不一致等)
> iOS 浏览器横屏时会重置字体大小，设置 text-size-adjust 为 none 可以解决 iOS 上的问题，但桌面版 Safari 的字体缩放功能会失效，因此最佳方案是将 text-size-adjust 为 100% 。

```css
.box{
  -webkit-text-size-adjust: 100%;
  text-size-adjust: 100%;
}
```

### flex布局

#### flex 最后一行左对齐

* 添加几个空item（对我来说最有效的，适用于大多数场景） 

> 根据布局列数添加空item，比如每行最大n列，那么在最后添加n-2个空item即可

```html
<style>
  .box {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  .item {
    width: 32%;
    height: 60px;
    margin-top: 10px;
  }
  .item-empty {
    height: 0;
    width: 32%;
  }
</style>
<body>
  <ul class="box">
    <li class="item"></li>
    <li class="item"></li>
    <li class="item-empty"></li>
  </ul>
</body>
```

* 利用after（适用于每行列数确定的场景）

```css
.box:after {
    content: "";
    flex: auto;
 }
```

### css Sticky Footer

> 如果页面内容不足够长时，页脚固定在浏览器窗口的底部；如果内容足够长时，页脚固定在页面的最底部。
> **总而言之，就是页脚一直处于最底**

* 方案一：margin-top

```css
.wrapper {
    height: 100%;
}
.content {
    width: 100%;
    min-height: 100%;
    padding-bottom: 50px;
    box-sizing: border-box;
}
.footer {
    margin-top: -50px;
}

// 这个方案需指定 html、body 100% 的高度，且 content 的 padding-bottom 需要与 footer 的 height 一致
```

* 方案二：calc

```css
.content {
    min-height: calc(100vh - 50px);
}
.footer {
    height: 50px;
}
```

* 方案三：Flex

```css
.wrapper {
    height: 100%;
    min-height: 100%;
    display: flex;
    flex-direction: column;
}
.content {
    flex: 1;
}
```



### 实现高度可控的分割线 ''|''

效果：

![](/partition.png)

```css
.reg:before {
    content: "";
    font-size: 0;
    padding: 10px 3px 1px;
    margin-left: 6px;
    border-left: 1px solid #ccc;
}
```

```html
<a href="">登录</a><a class="reg" href="">注册</a>
```



### 内联元素的垂直居中对齐

> **不受字体和字号影响**的内联元素的垂直居中对齐

![](/css2.png)

```css
.reload {
    display: inline-block;
    width: 16px;
    height: 1ex;
    background: url("./images/reload.png") no-repeat center;
}
```

```html
<li class="name">张三<i class="reload"></i></li>
```

