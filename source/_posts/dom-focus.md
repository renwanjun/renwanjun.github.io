---
title: 焦点管理
date: 2020-04-03 18:49:17
tags:
---
`document.activeElement` 这个属性始终会引用DOM中当前获得了焦点的元素。

元素获得页面的焦点的方式  
1. 页面加载  
默认情况下，当页面刚刚加载完成时，`document.activeElement`中保存的是`document.body`元素的引用。在文档加载期间，document.activeElementd的值是null。
2. 用户输入
通常是通过按<kbd>Tab</kbd>键
3. 代码中调用focus()方法
```javascript
var button=document.getElementById('reset');
button.focus();
document.activeElement===button; // true
```
4.`document.hasFocus()`用于确定文档是否获得了焦点。通过检测文档是否获得了焦点，可以知道用户是否正在与页面交互。