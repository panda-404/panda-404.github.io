---
title: js类型判断
date: 2018-05-16 12:24:56
tags: ['基础', 'js']
---
# js类型判断


今天才想起来漏写了类型检测，现在补上。。。
<!-- more -->

# 类型检测

在js中有6中数据类型：Number,String,Boolean,Null,Undefined,Object。有时候我们需要对值做类型检测，判断是原始值类型还是对象，是何种对象。这篇就总结下类型判断的常见方法。

## typeof

这是类型判断最基础的方法，能判断出number,string,boolean,undefined,object,function

```
var arr = [1, '1', false, null, undefined, {num:1}, [1], function(){}];
console.log(arr)
for(var i = 0, len = arr.length; i < len; i ++) {
 console.log(typeof(arr[i]));
} 

```

![类型检测](typeof.png)
可以看到用typeof检测时，将null也视为object，这是因为在以往null是用来给空对象占位的，但是在现在null意为这里不该有值。此外，虽然typeof能将function能将函数类型从object区分出来，但是比如日期对象、数组对象，typeof并不能区分。

## Object.prototype.toString

通过Object.prototype.toString可以返回一个`[Object 类型]`字符串。

```
var arr = [1, '1', false, null, undefined, {num:1}, [1], function(){}];
console.log(arr)
for(var i = 0, len = arr.length; i < len; i ++) {
 console.log(Object.prototype.toString.call(arr[i]));
}

```

![类型检测](toString.png)
可以自行试验一下，Object.prototype.toString可以判断几乎所有的数值与对象类型。
这里补充一下，直接调用toString方法会返回一个包含this指向的字符串。

```
var obj = {};
console.log(toString(obj));
console.log(window.toString(obj));
console.log(toString.call(null, obj));
console.log(toString(null));
console.log(toString(undefined)); 

```

![直接调用toString](toString1.png)

## instanceof

instanceof判断待检测值原型链上是否有对应构造函数的原型。这并不是一个完善的方法，因为对于原始值类型，并不存在原型。

```
var obj = {},
 arr = [];
function fn() {}
obj instanceof Object //true
arr instanceof Array //true
arr instanceof Object //true
fn instanceof Function //true
arr instanceof Function //false
fn instanceof Object //true

```

> 在谷歌控制台中，貌似为声明的对象进行instanceof和算术运算会被转换成空，如下
> ![控制台空对象](consoleObj.png)
> 原因虽然还不清楚，但是一般也不会直接在控制台进行操作。
> 本篇完。
