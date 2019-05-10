---
title: "［工具]-速查-Vim/Gvim常用操作"
date: 2019-05-10　14:45:00
categories:
  - Tools
tags:
  - VIM
  - GVIM
keywords: VIM, 速查, 替换, 批量, 查找,　设置,　显示
---

# Buffer操作

## 打开buffer
当使用命令vim或者gvim同时打开多个文件时，就会启动buffer，每一个文件都会放到一个buffer中，如命令
```
vim/gvim a.txt b.v c.c
```
同一个vim不同buffer之间的文件可以直接用`y` `p`命令拷贝内容，而不同vim间则需要通过系统剪切板
## Buffer之间跳转
- 跳转到下一个buffer : `: bn`
- 跳转到上一个buffer : `: b#` 注意，当首次执行buffer模式就执行这个命令的话因为vim不知道上一个buffer是什么，所以执行这条命令会出错
- 跳转到指定buffer   : `: b<1/2/3/...>` 注意'<>'不需要输入，只需要输入类似`b1`即可跳转到指定第几个buffer


## 向buffer添加新文件
- `:e filepath/filename` : 打开指定文件，将至放置入buffer中




# 跳转操作


## 跳转到指定行
直接输入`:行号`后回车即可跳到当前打开文件的指定行


## 在匹配符号间跳转
%在匹配的符号之间进行跳转，如 ( 调到对应的 ) 上



# SET命令以及vim设置

## 设置换行字符数

> textwidth[tw]  ： set tw=200【注意tw和200之间不能有空格】
> 是一种 word wrap 的功能，从左起算之固定每行的最大字符宽度。超过此宽度就会自动折行，这可是真的折行，也就是说在折行处会插入 EOL。预设是 0，也就是没有 word wrap 的功能。


## 设置tab相关

> 几乎所有的 OS 及软件都设定 Tab 就是 8 个字符长，这已经是个公认值，您硬要去改变它的话恐怕带来许多不便，但实际上关于程序风格，许多人又认为 8 个字符太长了，几个巢状循环下来就需折行，反而不方便。因此 Vim 体贴您，内建了 softtabstop 的功能，就是由 Vim 来代您制造出一个假的 Tab，实际上是空格符组成的 Tab。
> set shiftwidth=4 : 设置tab位宽为4
> set expandtab : 将tab转为对应个数的空格


将文件中的tab转成相应的空格：

```
%retab!
```


## 设置延时

```
set WD=200
```

------



* 使用以下命令可以将vim的代码保存到html，包括目前的配色以及格式

```
n1,n2 TOhtml
wq
```

其中，```n1```代表起始行号，```n2```代表结束行号，后面的```TO```是to的大写。```wq```命令可以将目前的转换结果保存到以此时代码为文件名的html文件，html可以直接拷贝到word中或者直接双击打开。

* 统计字符串个数

```
: %s/字符串/g
```

# 高亮

1. 取消选择高亮 ```nohl```- 当用诸如*进行高亮搜索后，如果想取消这些已经查找到的字符串高亮，则可以输入这个命令
2. 更改语法高亮
   有两种方式进行语法高亮，第一种是用set命令：


```
set filetype=java
```
    第二种有一些限制，需要先执行：


```
let do_syntax_sel_menu = 1|runtime! synmenu.vim|aunmenu &Syntax.&Show\ filetypes...

```

然后再才可以执行以下的命令，但是实际在测试的时候这两个命令都没有正确执行，所以最好的方式还是用第一种```set```命令

```
cal SetSyn ("verilog")
```



# 区块操作

1.```gv```- 重选之前已经选择的区域，比如之前已经选择了一块区域并且完成了编辑，想要再次编辑相同位置，则可以使用本命令

* 文件转换



1.将hex转为coe的步骤

```
%s/@\w*\s//g
```

2.将enc转为coe文件

```
%s/@\w*\s//g
```

------



# 删除操作  

1. 删除带有某字符串的行  

```
g/字符串/d
```
2. 删除不带有某字符串的行【保留带有某字符串的行】  

```
v/字符串/d
```

3. 删除重复行  

- 排序

:sort

- 查找重复行

/^\(.\+\)$\n\1


------



# 显示操作

## 打开以及关闭特殊字符显示

```
set list
set nolist
```



------



# 查找替换
vi/vim 中可以使用 :s 命令来替换字符串

- `:s/vivian/sky/`     :  替换当前行第一个 vivian 为 sky  
- `:s/vivian/sky/g`    :  替换当前行所有 vivian 为 sky
- `:n,$s/vivian/sky/`  : 替换第 n 行开始到最后一行中每一行的第一个 vivian 为 sky
- `:n,$s/vivian/sky/g` : 替换第 n 行开始到最后一行中每一行所有 vivian 为 sky
n 为数字，若 n 为 .，表示从当前行开始到最后一行
- `:%s/vivian/sky/`    :（等同于 `:g/vivian/s//sky/`） 替换每一行的第一个 vivian 为 sky
- `:%s/vivian/sky/g`   :（等同于 ```:g/vivian/s//sky/g```） 替换每一行中所有 vivian 为 sky
可以使用 # 作为分隔符，此时中间出现的 / 不会作为分隔符
- `:s#vivian/#sky/#`: 替换当前行第一个 vivian/ 为 sky/
- `:%s+/oradata/apras/+/user01/apras1+`: （使用+ 来 替换 / ）： /oradata/apras/替换成/user01/apras1/

## 实例

- `:s/vivian/sky/`: 替换当前行第一个 vivian 为 sky
:s/vivian/sky/g 替换当前行所有 vivian 为 sky
- `:n,$s/vivian/sky/`:  替换第 n 行开始到最后一行中每一行的第一个 vivian 为 sky
- `:n,$s/vivian/sky/g`: 替换第 n 行开始到最后一行中每一行所有 vivian 为 sky
(n 为数字，若 n 为 .，表示从当前行开始到最后一行)
- `:%s/vivian/sky/`: （等同于```:g/vivian/s//sky/```） 替换每一行的第一个 vivian 为 sky
- `:%s/vivian/sky/g`（等同于```:g/vivian/s//sky/g```） 替换每一行中所有 vivian 为 sky
可以使用 # 作为分隔符，此时中间出现的 / 不会作为分隔符
- `:s#vivian/#sky/#` : 替换当前行第一个 vivian/ 为 sky/

- 删除文本中的```^M```


> 问题描述：对于换行,window下用回车换行(0A0D)来表示，Linux下是回车(0A)来表示。这样，将window上的文件拷到Unix上用时，总会有个```^M```.请写个用在unix下的过滤windows文件的换行符(0D)的shell或c程序。

使用命令：```cat filename1 | tr -d “^V^M” > newfile```；


使用命令```：sed -e “s/^V^M//” filename > outputfilename```。需要注意的是在1、2两种方法中，^V和^M指的是Ctrl+V和Ctrl+M。你必须要手工进行输入，而不是粘贴。


在vi中处理：首先使用vi打开文件，然后按ESC键，接着输入命令：```%s/^V^M//```。


- `:%s/^M$//g`


如果上述方法无用，则正确的解决办法是：

 ```
tr -d "\r" < src >dest
tr -d "\015" dest
strings A>B
```


# 其它


利用 :s 命令可以实现字符串的替换。具体的用法包括：


`:s/str1/str2/`: 用字符串 str2 替换行中首次出现的字符串 str1
`:s/str1/str2/g`: 用字符串 str2 替换行中所有出现的字符串 str1
`:.,$ s/str1/str2/g`: 用字符串 str2 替换正文当前行到末尾所有出现的字符串 str1
`:1,$ s/str1/str2/g`: 用字符串 str2 替换正文中所有出现的字符串 str1
`:g/str1/s//str2/g`: 功能同上

从上述替换命令可以看到：g 放在命令末尾，表示对搜索字符串的每次出现进行替换；不加 g，表示只对搜索


字符串的首次出现进行替换；g 放在命令开头，表示对正文中所有包含搜索字符串的行进行替换操作

## 确认替换


使用搜索替换命令有时候会出错，而得到不想要的结果。所以小心并确认文件中需要修改的内容是一个明智的做法
在替换命令尾部加上**c** (confirm用于确认)，在替换每个old前都会提示并确认：
**：1, 30 s /old/new/ gc**
将会出现提示replace with hehe (y/n/a/q/l/^E/^Y)?  
y替换，n不替换，a替换所有，q放弃，l替换第一个并进入插入模式，^E和^Y是提示你用Ctrl+e或Ctrl+y来滚动屏幕的。
