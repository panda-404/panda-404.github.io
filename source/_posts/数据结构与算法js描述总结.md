---
title: 数据结构与算法js描述总结
date: 2018-05-21 14:33:24
tags: ['数据结构与算法', '读书笔记']
---
这篇作用是记录《数据结构与算法javascript描述》一书中的知识点和练习题
<!-- more -->
## 数组
数组定义是存储元素的线性集合，通过索引（元素地址的偏移量）存取元素
#### 存取函数
- 查找元素

  indexOf()返回参数在数组中的第一个索引

  lastIndexOf()返回参数在数组中的最后一个索引
- 数组字符串形式展示

  join()将数组按指定字符连接成字符串

  toString()以字符串形式显示数组
- 由已有数组创建新数组
  concat()合并两个数组

  splice()提取一个数组的子集

#### 可变函数
不引用数组中元素就可改变数组内容。
- 为数组添加元素

  push()添加元素到数组末尾

  unshift()添加元素到数组开头
- 从数组中删除元素

  pop()删除数组末尾元素

  shift()删除数组第一个元素
- 从数组中间位置添加和删除元素

  splice()
- 为数组排序

  reverse() 逆序 降序

  sort() 升序
> 排序时会调用数组元素的toString方法
#### 迭代器方法
为数组中每一个元素执行操作
1. 不生成新数组
- forEach
- every
- some
- reduce
2. 生成新数组
- map
- filter
> [数组练习题](https://github.com/zhangjunkunn/data-structures/blob/master/%E6%95%B0%E7%BB%84/index.js)
## 列表
#### 1. 列表抽象数据类型定义（ADT）
列表是一组有序的数据，适用于不需要排序，不是很长的序列。内部使用`listSize`保存列表元素个数、`append`在末尾添加元素、`insert`插入元素、`getElement`显示当前所在位置的元素，并封装了一系列迭代器方法如下图：
![列表抽象数据类型定义](列表抽象数据类型定义.png)

使用`pos`表示列表当前位置，通过改变这个属性读取列表中不同位置处的值。
列表定义的迭代器方法：`front end prev next currPos`，通过这些方法，可以不关心列表底层的数据存储结构对列表进行遍历，迭代器对访问提供了统一的方式。
```js
for(list.front(); list.currPos() < list.length(); list.next()) {
  print(list.getElement());
}
```
> 列表[定义](https://github.com/zhangjunkunn/data-structures/blob/master/%E5%88%97%E8%A1%A8/structor.js)及[练习题](https://github.com/zhangjunkunn/data-structures/blob/master/%E5%88%97%E8%A1%A8/index.js)
## 栈
栈是和列表类似的数据结构，区别是栈只允许在列表一端即栈顶添加或删除数据，栈是后入先出(LIFO last-in-first-out)的数据结构。js数组提供了模拟栈操作的方法`pop`和`push`。
1. 栈操作
- 入栈`push`
- 出栈`pop`
- `peek`展示栈顶元素
- 使用`top`属性记录当前栈顶位置
- `clear`清空栈，方式比较简单粗暴，将`top`设为0

栈这种先入后出的特性有比较多的应用: 进制转换、判断回文、递归、转换表达式、表达式中括号匹配等。这些还仅仅是书中粗浅的介绍。
> 栈[定义](https://github.com/zhangjunkunn/data-structures/blob/master/%E6%A0%88/structor.js)及[练习题](https://github.com/zhangjunkunn/data-structures/blob/master/%E6%A0%88/index.js)
## 队列
队列也是一种列表，与栈的区别是只能从一端（队尾）插入元素，从另一端（队首）删除元素。适用于存储有顺序排列的数据，先进先出（First-In-First-Out, FIFO）
队列实现和栈差不多，区别是一头进一头出。
