---
title: vim配置
date: 2017-03-30 16:30:54
category: 工作与学习
tags: vim
---

一直以来都是用vim作为开发工具，在这里记录一下我自己常用的vim配置
<!--more-->


![效果图](/assets/image/xiaoguo.png)

.vimrc文件：

```c
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

附：
[vim配置文件](/assets/vim.tgz)

