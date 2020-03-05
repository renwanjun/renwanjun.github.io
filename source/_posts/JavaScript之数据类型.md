---
title: JavaScript之数据类型
author: renwanjun
date: 2020-02-25 10:48:05
tags: JavaScript
categories:
    - Web大前端
    - JavaScript后花园 
---

先来了解一些基本概念
--------------------------------------
* 语法：ECMAScript语法大量借鉴了C及其他类C语言的语法
* 区分大小写：ECMAScript中的一切都区分大小写 变量、函数名和操作符
* 标识符：就是指变量、函数、属性的名字，或者函数的参数。标识符由字母、数字、下弧线_或一个美元符号$组成，首字母不能是数字。推荐采用驼峰大小写格式，例如firstSecond，可与内置的函数和对象名保持一致。
* 严格模式：ECMAScript5引入严格模式，为JavaScript定义了一种不同的解析与执行模型。要在整个脚本中启用严格模式，在顶部添加`"use strict"`。也可在指定函数在严格模式下执行，在函数内部的上方添加这条编译指示：
```
function doSomething(){
      "use strict"
      //函数体
}
```
* 变量：松散类型变量，所谓松散类型变量就是可以保存任何类型的变量。换句话说，**每个变量仅仅是一个用于保存值的占位符而已**。我们不建议修改变量保存值类型。

数据类型
=================================================
五种简单数据类型: Undefined,Null,Boolean,Number和String
一种复杂数据类型: Object
### typeof操作符
typeof操作符用于检测给定变量、数值字面量的数据类型

|  typeof操作符返回值   | 可能数据类型 |
|  ----  | ----  |
| undefined  | 如果这个值未定义 |
| boolean  | 如果这个值是布尔值 |
| string  | 如果这个值是字符串 |
|number|如果这个值是数值（12，NaN）|
|object|如果这个值是对象或者是null|
|function|如果这个值是函数|

>从技术角度讲，函数在ECMAScript中是对象不是一种数据类型。然而函数确实有些特殊的实行，因此通过typeof操作符区分函数和其他对象是有必要的。
### Undefined
值范围：只有一个特殊值undefined。
情况一：使用var声明一个变量但未对其初始化时，这个变量值就是undefined。
> 因此没有必要把一个变量的值显示地设置成undefined
```
var message;
aler (message==undefined);// true
```
情况二：尚未定义的变量
```
var message; // 这个变量声明之后默认取得了undefined值

alert(message) // "undefined"
alert(age) // 产生错误 
```
> 对于尚未声明过的变量，只能执行一项操作即实用typeof操作符检测其数据类型。（delete操作虽然不会报错，但是没有实际意义，且在strict mode下确实会报错）

### Null类型
数值范围：只有一个特殊值null
从逻辑角度看，null是一个空对象指针，而这正是使用typeof操作符检测null值会返回"object"的原因。
> 如果定义的变量准备在将来用于保存对象，那么最好将该变量初始化为null而不是其它值。如此只要直接检查null值就可以知道相应的变量是否已经保存了一个对象的引用。

实际上，undefined值是派生自null值的，因此：
```
alert(null==undefined); // true
```
尽管如此，两者用途完全不同不可混淆。
### Boolean类型
值范围：true 和 false
>注意：Boolean类型的字面值true和false是区分大小的，也就是TRUE和FALSE都不是Boolean值，只是关键字。

转型函数：Boolean()
ECMAScript中所有类型的值都有与这两个Boolean值等价的值。

| 数据类型 | 转换为true的值 | 转换为false的值 |
| ---- |---- |---- |
|Boolean|true|false|
|Undefined|n/a [^1] |undefined|
|Null||null|
|String|任何非空字符串|""空字符串|
|Number|任何非零数值|0和NaN|
|Object|任何对象|null|

[^1]:n/a(或N/A),是not application的缩写，意思是“不适用”
> 这些转换规则对理解 ***流控制语句*** 自动执行相应的Boolean转换非常重要。

### Number
