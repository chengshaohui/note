---
typora-copy-images-to: images
typora-root-url: images
---

# css笔记

## reset.css

```css
body {margin: 0;font:12px font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;;background: #fff;}
h1,h2,h3,h4,h5,p {margin: 0;}
ul ,ol {margin: 0;padding:0;}
li {list-style: none;}
a {text-decoration: none;}
img {display: inline-block; border: none;}
input,button{ margin:0; padding:0; outline: none;}
```

## mixin.css

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



## flex布局

### flex 最后一行左对齐

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
  .itemempty {
    height: 0;
    width: 32%;
  }
</style>
<body>
  <div class="box">
    <div class="item"></div>
    <div class="item"></div>
    <div class="itemempty"></div>
  </div>
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



## 实现高度可控的分割线 ''|''

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

## 内联元素的垂直居中对齐

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

