---
title: " [Tools]配置Atom(一)-为Atom增加Vim模式"
date: 2019-05-17　15:00:00
categories:
  - Tools
tags:
  - Tools
  - Atom
  - Vim
keywords: Atom, Vim, Github, 模式
---

# 第一章 为Atom增加Vim模式


[![Badge](https://img.shields.io/static/v1.svg?label=MyBlog&message=离场悲剧&color=<9cf>)](https://fpga1988.github.io)

Atom作为Github的配套编辑器在某些case下很方便，可以对一个repo进行很方便的管理，我会在写博客的时候使用Atom编辑器。而平时写代码习惯了Vim之后，总觉得Atom编辑起来还是太慢，因此，打算在Atom上安装一些插件，让其编辑时像Vim一样操作。

## 安装Vim模式插件
为Atom安装新插件很方便，直接打开`Settings`，然后找到`Install Packages`选项即可。
在搜索框中搜索`vim-mode-plus`，这个是`vim-mode`的加强版，其github地址为 https://github.com/t9md/atom-vim-mode-plus ，具体的feature以及安装注意事项可以参考项目的readme。
直接点击install即可安装，安装之后Atom即可自动支持vim模式，其实也就是移动、拷贝、跳转等操作，但是，还不支持命令操作，如:w,:s,:e等。

## 安装命令支持
搜索ex mode，然后安装`ex-mode`。安装之后，即可支持vim的相关命令。
