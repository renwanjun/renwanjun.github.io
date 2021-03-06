---
title: 闭包
date: 2020-03-02 12:49:15
tags:
---

## 执行环境和作用域
### 回顾作用域链的概念：

当某个函数被调用时，会创建一个执行环境及相应的作用域链，然后使用arguments和其它命名参数的值来初始化函数的活动对象。但在作用域链中，外部函数的活动对象始终处于第二位，外部函数的外部函数的活动对象处于第三位，直到作为作用域链终点的全局执行环境。  

### 执行环境和变量对象
每一个执行环境都有与之相对应的变量对象，全局环境的变量对象始终存在，而局部环境的变量对象在执行退出后就会自动销毁。

### 活动对象 
就函数而言，在函数执行的时候存在；

> 显然，作用域链本质上是一个指向变量对象的指针列表，它只引用但不实际的包含对象。


> this对象是在运行时基于函数的执行环境绑定的；在全局函数中，this等于window，而当函数被作为对象的方法调用时，this等于那个对象；匿名函数的执行环境具有全局性，因此其this通常指向window。

## 闭包的内存泄漏
闭包在IE9之前的版本中会导致一些特殊的问题。具体来说，如果闭包的作用域链中保存着一个HTML元素，那么意味着该元素将无法被销毁。