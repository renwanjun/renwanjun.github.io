---
title: html-rendering
date: 2020-03-16 13:02:20
tags:
---
浏览器渲染基本流程
====================================
GUI渲染进程
1.解析html文本并构建DOM tree  
2.解析CSS样式表并构建CSSOM tree  
3.根据DOM tree和CSSOM tree构建Render tree
4.根据Render tree信息进行布局处理(layout)
5.对页面元素进行绘制(painting)

### 解析(Parsing)
解析的过程分为两个步骤：词法分析（Lexical Analysis）和语法分析(Syntax Analysis)。
词法分析负责将输入内容分解成一个个有效标记；而语法分析负责根据语言的语法规则分析文档的结构，从而构建解析树(Parse Tree)。通过词法分析可以将无关的字符（比如空格和换行符）分离出来。

### 处理脚本和样式表的顺序
当浏览器碰到script脚本的时候
>>>
1.<script src="script.js"></script>

没有 defer 或 async，浏览器会立即加载并执行指定的脚本，“立即”指的是在渲染该 script 标签之下的文档元素之前，也就是说不等待后续载入的文档元素，读到就加载并执行。

2.<script async src="script.js"></script>

有 async，加载和渲染后续文档元素的过程将和 script.js 的加载与执行并行进行（异步）。

3.<script defer src="myscript.js"></script>

有 defer，加载后续文档元素的过程将和 script.js 的加载并行进行（异步），但是 script.js 的执行要在所有元素解析完成之后，DOMContentLoaded 事件触发之前完成。

### 脚本阻塞
### CSS的阻塞
