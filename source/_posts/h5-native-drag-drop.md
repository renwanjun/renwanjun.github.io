---
title: H5原生拖放
date: 2020-04-17 12:37:02
tags:
---
原生拖放的事件
================================
+ ie4:最早在网页中引入JavaScript拖放功能。当时在网页中只有两种对象可以拖放： 图像和某些文本。唯一有效的放置目标是文本框
+ ie5：拖放功能得到扩展，添加了新的事件，而且几乎网页中的任何元素都可以作为放置目标
+ ie5.5:让网页中的任何元素都可以拖放

HTML5以IE的实例为基础制定了拖放的规范，Firefox3.5、Safari4+和Chrome也根据HTML5规范实现了原生了拖放功能。可以在框架间、窗口见，甚至在应用间拖放元素。

------------------------------------------

##  拖放事件
拖动某元素时，将依次触发下列事件：
1. dragstart
2. drag
3. dragend

当某个元素被拖动到一个有效的放置目标上时，下列事件会一次发生：
1. dragenter
2. dragover
3. dragleave or drop

## 可拖动draggable
默认情况下，图像、链接和文本是可以拖动的。文本只有在被选中的情况下才能被拖动，而图像和链接在任何时候都可以拖动。
让其它元素可拖动，H5为所有元素规定了一个draggable属性，表示元素是否可以拖动。要想让其它元素可拖动，或者让图像或链接不能土洞，都可以设置这个属性。  
例如：

    <!-- 让这个图像不可拖动 -->
    <img alt="Smiley face" draggable="false" src="smile.gif">
    <!-- 让这个元素可以拖动 -->
    <div draggable="true">...<div>
> 兼容性
> + 为了让FireFox支持拖动属性，还必须添加一个obdragstart事件处理程序，并在dataTransfer对象中保存一些信息。
> + 在IE9及更早版本中，通过mousedown事件处理程序调用dragDrop()能够让任何元素可拖动。
> + 而在Safari4及之前版本中，必须额外给相应元素设置CSS样式```-khtml-user-drag:element```.

## 自定义放置目标
虽然所有元素都支持放置目标事件，但这些元素默认是不允许放置的。如果拖动元素经过不允许放置的元素，无论用户如何操作都不会发生drop事件。不过可以将任何元素变成有效的放置目标，方法是重写dragenter和dragover事件的默认行为。例如，假设又一个ID为“droptarget”的\<div>元素,可以用如下代码将它变成一个放置目标：

    var droptarget=document.getElementBtId('droptarget');
    droptarget.addEventListener('dragenter',function(event){
        event.preventDefault()
    })
    droptarget.addEventListener('dragover',function(event){
        event.preventDefault()
    })
> FireFox3.5+中，放置事件（drop）的默认行为是打开被放到拖置目标上的URL。换句话说，如果是把图像拖放到放置目标上，页面就会转向图像文件；而如果是把文本拖放到放置目标上，则会导致无效的URL错误。因此，为了让FireFox支持正常的拖放，还需要取消drop事件的默认行为，阻止它打开URL。

## dataTransfer对象
### getData()和setData()方法
+ getData()
+ setData()

```javascript
// 设置和接受文本数据
```
### dropEffect和effectAllowed属性
> dropEffect属性可以知道被拖动的元素能够执行哪种放置行为。
+ "none"
+ "move"
+ "copy"
+ "link"
> 要使用dropEffect属性，必须在ondragenter事件处理程序中针对放置目标来设置。dropEffect属性只有搭配effectAllowed属性才有用。
> effectAllowed属性表示允许拖动元素的哪种dropEffect.

> 必须在ondragstart事件处理程序中设置effectAllowed

