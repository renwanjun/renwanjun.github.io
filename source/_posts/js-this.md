---
title: JavaScript之this到底是什么
date: 2020-02-10 21:19:10
tags: JavaScript
categories: 
    - Web大前端
    - JavaScript后花园 
---
前言
=============
this对象是在运行时基于函数的执行环境绑定的；在全局环境中,this等于window,而当函数被当作某个对象的方法调用时，this指向这个对象。而匿名函数执行时this通常都是指向window,除非显示使用call、apply、bind绑定执行对象。

***关于this的来源***
每个函数在被调用时都会自动取得两个特殊变量：this和arguments。内部函数在搜索这两个变量时，只会搜索到其活动对象为止，因此永远不可能直接访问外部函数中的这两个变量。
## 全局函数中的this
## 对象的方法中的this
## 闭包中的this
## 箭头函数中的this

## 绑定this