---
title: " [ASIC] 使用Verdi进行ECO流程"
date: 2019-06-04　15:12:00
categories:
  - ASIC
tags:
  - ASIC
  - Tool
  - Verdi
  - ECO
keywords: ECO, 流程, ASIC, Verdi
---

# 使用Verdi进行ECO的流程

> 一场提升自我的旅行

[![Badge](https://img.shields.io/static/v1.svg?label=MyBlog&message=离场悲剧&color=<9cf>)](https://fpga1988.github.io)

## 背景
在IC设计中，因为设计缺陷导致的改版是一个很难避免的事情。某些bug的修复需要对rtl改动很大，这样的改版就需要把前端所有的flow都全部重新来一遍。而有一些则只需要更改较少逻辑就可以修改成功，这个我们就可以靠eco进行修复。而最近我做的一颗芯片就遇到了这样的情形，因此，写下此篇，对ECO及其方法进行简单介绍。


## 什么是ECO？
ECO是Engineering Change Order的缩写，中文翻译过来就是工程改变命令。如果bug出现在tape-out之前，只要时间上来得及，我们都可以通过修改rtl的方式来进行bug修复，但是如果发生的时间点距离最后sign off的时间很近，或者说在芯片回来后我们才发现bug，那么想通过最小的大家来进行bug修复，那么就会优先尝试ECO方案。

## ECO可修复的BUG类型
ECO可以对连接性bug、简单逻辑bug、驱动能力bug、时序、串扰等问题进行修复。针对需要修改逻辑的bug，需要使用芯片中的spare cell，这也是我们在芯片设计的时候放置一部分数字spare gate的原因，一旦发现bug，我们可能可以通过这些gate来进行bug修复，降低费用时间消耗。我们这里主要讲一讲怎么通过spare gate进行bug修复。

## Verdi ECO工具简介
Verdi是一个IC的综合debug平台，它的主要作用是进行数字逻辑的代码、波形分析，于此同时，它还包含有我们这里提到的ECO功能。对于简单逻辑的ECO，我们可以通过人工进行网表修改，而面对日益复杂的设计，网表通过人工很难梳理清楚，不小心还会出现错误，因此，nECO就是用于解决这个难题，它可以将你想做ECO的逻辑和其他无关逻辑隔离开，这样你可以很简单的进行修改。修改完成后，你可以进行commit，然后保存eco结果。

## nECO的功能
nECO具有以下功能：
- 专用ECO窗口用于隔离需要修改的逻辑
- 修改逻辑门连接
- 增加或者删除逻辑门
- 提交修改
- freeze和non-freeze模式的支持
- 脚本支持
- 增加删除buffer
- 重命名

## ECO实例
在本实例中，出现了这样一个bug：寄存器复位端因为驱动能力不足的原因导致前端输入时一个800ps的低脉冲，经过一个buf后连接到n个寄存器，这个寄存器的复位信号没有产生低脉冲。现在，我们要通过ECO工具对复位信号添加buf，以增强其驱动能力。

### 导入设计
第一步是将网表文件、sdf文件一同导入，这里实际上用不到sdf文件。使用import菜单进行设计的导入，导入PR后的网表，于此同时，使用`-v .../xx.v`选项进行库模型文件的指定，这样不用将库也当做verilog文件进行导入。

使用File菜单的SDF中的`Load SDF File`进行sdf文件的导入

### 
