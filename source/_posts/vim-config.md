---
title: vim配置与使用
date: 2017-03-30 16:30:54
category: 工作与学习
tags: vim
---

一直以来都是用vim作为开发工具，在这里记录一些常用的vim命令和我自己的vim配置

<!-- more -->

## vim配置

附：[vim配置文件](/assets/vim.tgz)

将.vimrc文件放到用户根目录 ~ ，再将主题文件Tomorrow-Night-Eighties.vim放到 ~/.vim/colors/ 就可以得到如下图所示的 vim 配置效果。

![效果图](/assets/image/xiaoguo.png)

vimrc配置：

```c .vimrc
" 自动缩进
set autoindent
" C语言风格缩进
set cindent
" 语法高亮
set syntax=on
" 显示行号
set number
" 高亮搜索
set hlsearch
" 背景颜色
set background=dark
" 记住上次访问位置
au BufReadPost * if line("'\"") > 1 && line ("'\"") <= line("$") | exe "normal! g'\"" | endif
" 如果是C文件，设置以下参数
autocmd FileType c set tabstop=4 shiftwidth=4 softtabstop=4 expandtab
" 设置背景256色
set t_Co=256
" 设置主题
colorscheme Tomorrow-Night-Eighties
" 设置状态栏数
set laststatus=2
" 设置ctags自动遍历
set tags+=tags;
set autochdir
" 高亮当前行
set cursorline
"hi Cursorline cterm=NONE ctermbg=237
" 自动启用Tlist
"let Tlist_Auto_Open=1
let Tlist_Exit_OnlyWindow=1

" 按键映射
:map <F1> :Tlist<CR>
:map <F2> :set tabstop=4<CR>
:map <F3> :set tabstop=8<CR>
```

## vim常用命

以下所有命令都是在命令行模式下使用

### 跳转

`gg` 跳转到第一行

`G` 跳转到最后一行

`ngg 或 nG 或 :n` 跳转到第n行

### 查找

`/string` 查找匹配string，按 n 向下匹配，N 向上匹配

`/\<string\>` 查找全字匹配string

快捷键 shift + 8：查找光标所对应的字符串

### 替换

`:s/str1/str2/` 替换当前行第一个 str1 为 str2

`:s/str1/str2/g` 替换当前行所有 str1 为 str2

`:m,ns/str1/str2/` 替换第m行到第n行第一个 str1 为 str2

`:m,ns/str1/str2/g` 替换第m行到第n行所有 str1 为 str2

`:%s/str1/str2/` 替换每一行第一个 str1 为 str2

`:%s/str1/str2/g` 替换每一行每一个 str1 为 str2

### 分屏

在分屏之间切换窗口：按住 ctrl 然后双击 w

**在已经打开文件 file1 的情况下，想打开文件 file2:**

`:sp file2.c` 垂直分屏打开 file2 文件

`:vsp file2.c` 水平分屏打开 file2 文件

**未开启vim的情况下，想同时打开文件 file file2:**

`vim -o file1 file2` 水平分屏打开 file1 file2 

`vim -O file1 file2` 垂直分屏打开 file1 file2
