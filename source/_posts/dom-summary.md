---
title: dom-summary
date: 2020-04-03 18:42:15
tags:
---
>document部分对html节点的直接引用
+ `document.head` 引用文档的`<head>`元素
```javascript
var head=document.head || document.getElementByTagName('head')[0]
```

+ `document.body`
+ `document.doctype`
+ `document.forms`
+ `document.images`
+ `document.iframes`
+ `document.activeElement` HTML5新增 这个属性始终会引用DOM中当前获得了焦点的元素

> 状态
+ `document.compatMode` 判断渲染页面的模式，返回值：  
"CSS1Compat"——标准模式
"BackCompat"——混杂模式
