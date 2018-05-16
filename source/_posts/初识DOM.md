---
title: 初识DOM
date: 2018-05-16 12:18:55
tags: ['DOM', '基础']
---
# 初识DOM

前几篇简略的将js的知识复习了一遍，不过还有很多方法、函数式、ES5,6的新特性没概括，之后再补充吧。现在开始了解前端的另一个核心–DOM
<!-- more -->
DOM是`Document Object Model`的简写，主要功能是用以操作文档，文档能够被操作，是因为在解析页面时将文档结构创建为`document`对象，html文档中的一个个标签以`html`节点为根节点构建为有父子结构的树状结构，将文档中的标签转变为可以操作的节点。
![节点树](DOMtree.jpg)

# 针对节点的操作

## 查找节点

节点查找常见有以下方法
```
//选出实时变化的元素类数组
document.getElementsByTagName()
document.getElementsByClassName()
document.getElementById()

//选出非实时变化的元素类数组
document.querySelector()
document.querySelectorAll() 

```

## 添加节点

```
document.createElement()
document.createTextNode()
document.createComment()

```

## 插入节点

```
//注意这两种方法都有剪切作用
parent.appendChild(child)
//在next前插入pre
parent.insertBefore(pre,next)

```

## 删除节点

```
//removeChild也有剪切作用，返回被删除节点
parent.removeChild(child)
child.remove()

```

## 替换节点

```
//new替换origin同时返回origin
parent.replaceChild(new, origin)

```

document对象上还定义了一些其他属性方法如：

```
document.write() //重写整个文档
document.open() //擦除当前文档并新开一个文档
document.close() //关闭当前文档
document.anchors //文档中锚点的集合
document.domain //设置或返回当前文档域名
document.title //当前文档标题

```

# 节点属性

每个节点都可以当作一个对象，提供了大量属性和方法，不仅仅能够操作节点本身，就不一一介绍了。
 
```
node.innerHTML
node.attributes
node.getAttribute()
node.setAttribute()
node.lastChild
node.nextSibling
node.offsetHeight
node.parentNode
node.style

```
