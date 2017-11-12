---
title: HTML标签简介
date: 2017-10-30 20:30:19
tags: [html]
---
# HTML标签
## 1. 文档声明
`<! DOCUTYPE >` （不是一个标签）文档声明头DTD（docutype declaration）有如下几种形式
 
*用于XHTML1.0严格模式的*
```html
<!DOCTYPE htmlPUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
```
<!--more-->
*用于XHTML1.0过渡模式*
```html
<!DOCTYPE htmlPUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

*但是现在通用HTML5的文档声明模式*
```html
<!DOCUTYPE html>
```
前几种因为标记语言基于SGML，故需要引入文档类型声明DTD，HTML5没有基于SGML，所以文档声明大大简化了

## 2.根标签<html></html>
页面中的其他标签需要放在根标签里
## 3.头标签<head></head>
`<head></head>`标签，其中可以包含描述页面信息的标签，可用于SEO优化，可包含如下标签

`<title></title>`页面标题

`<meta />`提供页面的基本信息，元配置
可以设置页面的配置信息，例如`charset`可以设置页面支持的字符集，避免出现不支持的字符时乱码，charset的字符集必须和文档保存的文件编码类型一致，具体引入`utf-8`还是`gbk2312`，考虑加载速度和字符集数量。meta标签也可用于设置页面的关键字内容。

`<meta name="Description" content="描述内容" />`告诉搜索引擎页面的描述

`<meta name="Keyword" content="关键字" />`告知页面的关键字

`<link />`引入外部资源如css

`<script></script>`包含或者引入js脚本
## 4.body标签
`<body></body>`存放页面主要内容，可以配置一些属性，如`bgcolor`背景色，`background`背景图片，`text`文本颜色，`topmargin`上边距，`link`超链接默认颜色，`alink`链接被点击时的颜色，`vlink`点击完成后的颜色，不过避免这样使用，与web规范违背。
## 5.其他语义化标签
作为一门标记语言，HTML中的标签语义化都十分好，例如`<p></p>`即为paragraph

按标签元素类型有如下分类：
1. 块级元素：属性为`display: block`的标签，可以设置宽高，独占一行，不能继承自行级元素，即不能嵌套在行级元素中。块级元素一般来说可以包含任意元素，但是像`<p></p>`标签这样文本级标签，只能包含文字、图片、表单元素等具有文属性的内容
```
常见的几个块级元素：
address -- 地址
blockquote -- 块引用
div -- 最常用的块级容器
form -- 表单
table -- 表格（里面嵌套<tr>和<td>标签）
h1~6 -- 1~6级标题
hr -- 水平线
ol -- 有序列表
ul -- 无序列表
p -- 段落标签
```
2. 行级元素（内联元素）：属性为`display: inline`的标签
```
常见的行级元素：
a -- 锚点
em -- 强调
u -- 下划线
cite -- 引用
br -- 换行
i -- 斜体
img -- 图片
label -- 表格标签
span -- 最常用内联容器与div标签类似
input -- 单行文本输入框
textarea -- 多行文本输入框
```
> 随着web规范的完善，行为样式结构分离的提出，很多标签已经不推荐使用，这些不用得标签可用于自定义标签

3. 行级块元素：属性为`display: inline-block`的标签，兼具行级元素与块级元素的特性，不属于默认`display`属性的一种，使元素本身解析为`inline`，内部解析成`block`
> tips: 凡是带有inline属性的元素均带有文字属性，元素之间会有4px的间距。

按照元素渲染出的盒模型可以分为如下：
1. 容器级元素： 可以嵌套任意元素
2. 文本级元素：只能嵌套文本、图片、表单元素。如果在文本级元素中嵌套了块级，则会自动先将文本级元素标签闭合一次，例如：
```
<p>
    <div>嘿嘿</div>
</p>
<!--  在页面中会渲染成如下形式 -->
<p></p>
<div>嘿嘿</div>
<p></p>
```
#### `<span>`&`<div>`
这是HTML中重要的两个容器标签，作用相当于抽屉或是收纳盒，可以划分页面具有不同功能的区域，便于存放和操作其他标签，区别是`<div>`是块级元素，独占一行，`<span>`行级元素，内容决定其宽高，多用来容纳文字。
#### 这里需要提一下`<a>`标签，锚点标签
这也是HTML中重要的一个标签，
`<a href=""></a>`属性`href`意为hypertext reference，超文本引用，可以实现如下功能：
1. 链接：`<a href="http://www.baidu.com">`点击既能跳转到百度。
2. 锚点：`href`这个用法需要配合`name`或者`id`属性：
```
<div id="up"></div>
<a href="#up">
<!-- 点击a可以定位到div -->
```
3. 协议限定符：`href`属性还可填写一段javascript代码，点击就执行
```
<a href="javascript: alert('点击了a')">
<!-- 点击会弹出警示框 -->
```
4. 除此之外，`href`还可实现电话，邮件的功能
```
<a href="mailto:邮箱地址">
<a href="tel:电话号">
```
5. `target`属性：规定了打开目标页面的方式
```
_self -- 在当前窗口打开
_blank -- 在新窗口打开
```
> 但是这些功能均可用js实现，故不推荐直接使用

#### 图片标签`<img />`
这是一个单标签，主要属性`src`，用于引入图片位置，可填写*相对路径*，*绝对路径*，*服务器路径*，`alt`属性，图片占位符，用于图片无法显示时提示图片信息，可被搜索引擎爬虫识别

*相对路径*：和页面相同文件夹目录下的路径
```
<img src="one.jpg" /> -- 当前目录下
<img src="./one.jpg" /> -- 当前目录下
<img src="images/one.jpg" /> -- 当前目录下images文件夹下
<img src="../images/one.jpg" -- 上一级目录的images文件夹下
```
*绝对路径*：图片完整的引用路径
`<img src="C:/desktop/one.jpg" />`

*服务器路径*：`<img src="/images/one.jpg" />`以imgages为根目录向下寻找

#### 有序列表，无序列表
有序列表`<ol></ol>`，无序列表`<ul></ul>`多用来做具有归属关系的功能块、子项，两者区别是子项有无顺序，子项`<li></li>`，可以在`<ul></ul>`上添加`type`属性实现子项的样式：
```
默认样式 disc -- 小圆点
square -- 实心正方形
circle -- 空心圆圈
```
对于有序列表`<ol></ol>`可通过设置`type`属性来规定排序方式，`reversed`反向排序，`start`开始位置
#### 表单<form></form>
表单常用于与后台进行数据传送
```
一个简单的账号密码：
<!-- method表示数据传送的方法，有get和post两种，action是数据发送的地址 -->
<form method="get" action="#">
<!--input标签的type属性表示文本类型，text明文，password暗文，name表示数据名，value对应数据值-->
    username: <input type="text" name="username" value="填写用户名">
    password: <input type="password" name="password">
    <input type="submit" value="确定">
<!--input的type值为submit时代表这是一个提交按钮，
可配置value属性显示按钮的文字，默认提交，
点击按钮会触发表单的submit事件-->
<!--input的type值还有上传文件的file，
需要搭配form上的属性enctype="multipart/form-data"
默认情况下，type="application/x-www-form-urlencoded"
</form>

<!--input也可做选择框-->
<form method="get" action="#">
    male:<input type="radio" name="sex" value="male" checked>
    female:<input type="radio" name="sex" value="female">
<!--radio表示单选框，checkbox多选框，设置相同的name表示一组选项，checked默认选中-->
</form>

<!--下拉选择框-->
<form method="get" action="#">
    <select value="北京">北京</select>
    <select value="上海">上海</select>
<!--value才是真实的数据值，默认选中第一个select的内容-->
</form>
```
## 6.特殊字符
在HTML中输入多个空格会被折叠为一个空格：
```
<div>嘻      哈哈哈哈</div>
<!--  渲染到文档中时,多个空格会合并为一个 -->
嘻 哈哈哈哈!
```
并且，当你想在页面中直接输出一个标签`<div>`是不行的，浏览器会将它当作HTML渲染，正确的做法是将`<`用特殊格式表示：
```
举栗子
&nbsp; -- 空格
&gt; -- >号
&lt; -- <号
&amp; -- &
&quot; -- "号
&apos; -- '号
&copy; -- 版权符号 ©
&trade; -- 商标 ™
&#[五位字符unicode码]; -- 可用这种形式输出特定字符
```
***
## 结语
HTML的常用标签部分大致就这么些，当然HTML中的标签多种多样，尤其2014年HTML5的推出引入了多种类似`<div>`但是语义化更加明确的标签，如`<header>`定义文档头部，`<footer>`表示文档等页脚，`<article>`一段文章，`<aside>`侧边栏，`<section>`文档的一小节，等等，使页面具有更好的语义和结构。