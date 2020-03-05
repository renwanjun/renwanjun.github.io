---
title: NPM常用命令
date: 2020-03-02 15:25:31
tags: [npm,command]
categories:
  - Tool
---

## 基本命令

### 查看

    $ npm ls [过滤条件]

使用这个命令查看所有发型包列表和它们的版本，过滤条件可选，或者几个过滤条件结合查看。

    $ npm ls installed // 查看已经安装的Node包
    $ npm ls stable    // 产看所有稳定版的发型包
    $ npm ls installed stable //结合过滤条件查看
    $ npm ls fug //按照模块名称查看
    $ npm ls @1.0 
### 安装
    $ npm install package[@过滤条件]
使用这个命令可以安装一个指定的包

    $ npm install 包的名称 //安装指定包
    $ npm install 包的名称@版本号 //安装指定版本的
    包
    $ npm install 包的名称@>=版本号 //结合版本号和范围安装

### 删除包
    $ npm rm sax //删除包的所有版本
    $ npm rm -g express //删除以全局模式安装的包

### 查看包的信息
    $ npm view connect 
    $ npm view connect@1.0.3 //查看特定版本的包的信息

## package.json文件

### 版本号

主版本.次版本.补丁版本号
例如 1.12.3  
既然补丁版本号仅仅是修复一些程序bug,指定主版本号和次版本号，不限定补丁版本号就是一个常用的方法。如：1.23.x
