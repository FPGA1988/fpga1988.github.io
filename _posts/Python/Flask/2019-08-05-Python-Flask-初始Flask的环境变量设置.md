---
title: "[Python]-Flask-初始Flask项目的环境变量设置"
date: 2019-08-02　15:00:00
categories:
  - Python
  - Flask
tags:
  - Python
  - Flask
  - 环境变量
keywords: Python, Flask, 环境变量
---
# 环境变量的管理

## 环境变量的分类
环境变量分为临时环境变量和永久环境变量，临时环境变量会在当前终端/窗口结束后被清除，而永久环境变量写到注册表/系统中，即使系统重启也不会丢失。在Windows系统和Linux系统中，要批量、快速设置临时环境变量都比较简单，但是在Windows中，要快速批量设置永久系统环境变量比较复杂，对于Flask的应用，并没有强烈需要设置永久环境变量，因此推荐采用临时环境变量

## 传统环境变量管理
传统的环境变量设置是通过系统命令进行，例如使用export或者set命令等，这样管理的缺点是对于不同的系统平台如linux何windows，可能有不同的命令进行设置。因此，推荐使用python的虚拟环境变量管理包`python-dotenv`进行环境变量的管理。
## 虚拟环境变量管理

### 安装管理包
使用以下命令安装环境变量管理包:
`pip install python-dotenv` 或者 `pipenv install python-dotenv`

### 创建环境变量分类


### 设置环境变量

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
