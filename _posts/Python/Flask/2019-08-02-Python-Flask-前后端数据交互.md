---
title: "[Python]-Flask-前后端数据交互"
date: 2019-08-02　15:00:00
categories:
  - Python
  - Flask
tags:
  - Python
  - Flask
  - 数据交互
keywords: Python, Flask, 前端, 后端, 数据交互, POST
---
# Flask前后端数据交互

在Flask的web应用中，在前后端之间，经常有需要进行数据交互，将用户传入的命令或者数据传到后端进行处理，或者说将后端处理的结果或者查询的结果返回到前台使用或者显示，下面，将分别从几个应用方面对常用交互方法进行说明

## 点击动作传到后端
无论是点击文字、按钮亦或者是菜单等，都可以将这个动作传送给后端，点击后让后端进行一些想要的操作。要实现这一功能，需要在前后端分别进行以下设置:
- 前端
  使用<a href="view函数路径"></a>进行后端对应的注册路由路径，例如，后端注册路由为: @xx_bp.route('/xx/def_name',******),那么，这里的view函数路径为"xx.def_name"
- 后端
  1. 注册路由 : @xx_bp.route('/xx/def_name', methods=['GET', 'POST'])  
  2. 视图函数 : def def_name:  

## 表单数据传到后端



## 返回简单信息传到前端
直接在视图函数中使用return进行信息返回，例如:
```Python
def a_name:
  ...
  return("Operation Done")
```
这样在前端就可以显示一个网页，其内容为return的内容
## 返回表单数据到前端



## 返回文件到前端
