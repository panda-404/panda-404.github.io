---
title: CSS简介
date: 2017-10-30 20:30:35
tags: [css]

---
## 1.简介
CSS全称Cascading Style Sheet层叠样式表，它的提出是为了解决一开始HTML各种显示功能的发展导致了HTML页面混乱臃肿。CSS的作用是定义HTML等文件的样式，使样式和页面结构分离开，便于之后再次更改样式。就如同html文件是一个涂色本，你可以任意规定某个部分的颜色，页面的表现不在和页面结构相关。CSS的内容主要分为选择器和样式属性。
<!--more-->
## 2.CSS引入
一般CSS有三种引入页面的方式：
```
1. 页面级css
<head>
    <style type="text/css">
<!--style的type属性规定了文件的数据类型(MIME)，
这儿type只有唯一值text/css，现在可以忽略type属性，
style标签的默认type类型为text/css-->
        div {
            height: 100px;
            width: 100px;
            background-color: red;
        }
        @import url(CSS文件地址)
        <!--import方式引入的CSS文件里的代码-->
    </style>
</head>

2. 以行间样式引入CSS
<div style="height: 100px;width: 100px;background-color: red;">
</div>

3. 引入外部CSS文件（推荐方法）
<head>
    <link rel="stylesheet" type="text/css" href="page.css">
    <!--rel是引入文件与页面之间的关系，
    stylesheet作为当前页面的样式表，
    href是外部资源的地址-->
</head>
```
## 3.选择器
CSS提供了多样的选择器使CSS样式与html结构匹配，有这样一个结构：
```html
<div class="container" id="only">
    <div class="header">
        <ul class="ul-list">
            <li class="first">one</li>
            <li>two</li>
            <li>three</li>
        </ul>
        <span>
            <em>我在这儿</em>
            <strong>我也在这儿</strong>
        </span>
    </div>
    <div class="footer">
        <p>这是一行文本</p>
    </div>
</div>
```
下面就演示下CSS中的选择器。
1. 标签选择器
```
em {
    color: green;  //我在这儿变为绿色
}
div {
    border: 1px solid black; //页面中所有div增加1px边框
}
```
2. class选择器
```
.header {
    background-color: red; //类名为header的div背景色变为红色
}
```
3. id选择器
```
#only {
    width: 500px;
    height: 500px;  //id为only的标签有500*500宽高
}
```
4. 通配符选择器
```
* {
    margin: 0px;
    padding: 0px;  //页面中所有标签去除内外边距
}
```
5. 父子选择器
```
.header ul li {  //选中类名为header的div下的ul的子元素li
    background-color: blue; 
}
//父子选择器查找顺序，从子元素向父元素查找
//先找到li，再筛选出父元素为ul的li，逐级向上查找
```
6. 并列选择器
```
li.first { //选中有类名first的li
    background-color: yellow;
}
```
7. 分组选择器
```
.header span em,
.header span strong { //同时选中div.header下span下的em和strong
    color: pink;
}
```
8. 伪类选择器
```
为什么叫伪类呢？是因为这个选择器的效果和手动添加一个类名来选择，
效果是一样的。
a:hover {
    background-color: skyblue;
}
//效果和在a标签上添加了一个class="hover"的类是一样的
```
> CSS2.0大致就这七种选择器，CSS3.0又推出了属性选择器，伪元素选择器，条件选择器等

一般来说页面中当然不会只有这么点样式，那么当多个样式同时作用到同一元素时，怎么判断元素最后呈现的样式呢
```
<div style="width: 100px;height: 100px;" class="demo" id="test"></div>
<!--css-->
div {
    height: 200px;
    width: 200px;
}
.demo {
    height: 300px;
    width: 300px;
}
#test {
    height: 400px;
    width: 400px!important;
}
//div最后宽400px高100px
```
之所以会这样，是因为引入了一个CSS权重的概念，权重值如下：
```
!important  --  infinity
行间样式  --  1000
id选择器  --  100
属性/class/伪类选择器  --  10
标签/伪元素  --  1
通配符  --  0
//需要判断最终样式时，按照权重值大小判断，越大优先级越高
//当权重值相同时，在样式表中后出现的样式会覆盖先出现的
```
## 4.CSS的一些属性
CSS的属性按照功能可以分为字体文本、边框、背景、盒模型、颜色、定位布局、边距等方面的属性，只简单介绍几种，详细的可以参考手册或是上W3C index查找。
```
font-famliy -- 字体，可以填写多个字体用于兼容
font-size -- 字体大小，默认字体大小16px,网页一般12px
color -- 字体颜色，有三种表示方法，颜色英文单词，十六进制表示，rgb(a)函数表示
text-align -- 文本水平对齐方式
text-indent -- 首行文字缩进
text-decoration -- 文本装饰样式
verticla-align -- 垂直对齐方式（基准线）
letter-spacing -- 文字间隙
word-spacing -- 单词间隙
border -- 边框，这是一个复合属性，由三种属性复合
border-width -- 边框宽度
border-style -- 边框样式(solid,dotted,dashed)
border-color -- 边框颜色
border-left/right/top/bottom -- 单独设置某一边框
background -- 背景，复合属性
background-repeat -- 背景图片没全部填充时是否重复
background-size -- 背景尺寸支持数字、百分比、cover、contain
background-attachment -- 定义背景图随滚动条滚动方式
background-clip -- 背景图片开始绘制区域
display -- 元素展示形式
list-style-type -- 列表元素样式
list-style-position -- 列表标号位置，是在内容器区还是ul内边距区
position -- 定位
visibility -- 可见性
overflow -- 溢出是否隐藏
```
> 这里仅仅笼统提一下CSS2、3中的属性，CSS布局是前端领域的重难点，建议看看张鑫旭大神的各种奇技淫巧。
