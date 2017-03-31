---
title: Linux内核编程规范
date: 2017-03-31 14:42:42
category: 工作与学习
tags: 	
    - c 
    - linux
---

参加工作以后，公司没有规定编程语言的规范，所以我就参考了[Linux kernel coding style][1]作为编程规范。

## 1. 缩进

* 缩进采用8个字符宽度的tab

* switch和case对齐
```c
switch (suffix) {
case 'G':
case 'g':
	mem <<= 30;
	break;
case 'M':
case 'm':
	mem <<= 20;
	break;
case 'K':
case 'k':
	mem <<= 10;
	/* fall through */
default:
	break;
}
```

## 2. 行长度限制

* 代码行长度要在80以内

## 3. 括号和空格的位置

### 括号
* 下列非函数关键字，左大括号"{"不用换行
**if, switch, for, while, do**
```c
if (x is true) {
	we do y
}
```

* 函数的左大括号"{"要换行
```c
int function(int x)
{
	body of function
}
```

* 以下情况右大括号"}"不单独占一行
```c do-while
do {
	body of do-loop
} while (condition);
```
* ```c if-else
if (x == y) {
	..
} else if (x > y) {
	...
} else {
	....
}
```

* 单行不需要使用大括号
```c
if (condition)
	action();

if (condition)
	do_this();
else
	do_this();
```

### 空格

* 下列关键字后面使用一个空格
**if, switch, case, for, do, while**

* 定义指针类型时，"*"紧靠变量名或函数名
```c
char *linux_banner;
unsigned long long memparse(char *ptr, char **retptr);
char *match_strdup(substring_t *s);
```

* 下列二元和三元操作符左右各留一个空格
**=  +  -  <  >  *  /  %  |  &  ^  <=  >=  ==  !=  ?  :**

* 下列一元，自加减，结构体成员的操作符不留空格
**&  *  +  -  ~  !  sizeof  typeof  alignof  __attribute__  defined**
**++ --**
**. ->**

* 不要在行尾留有空格，Git会警告行尾含有空格的patch

## 4. 命名

* 全局变量要有描述性的名字
例如活跃用户统计函数应该命名为**count_active_users()**而不是**cntuser()**

* 局部变量命名要简短
例如循环计数变量应该命名为**i**而不是**loop_counter**

## 5. Typedefs

## 6. 函数

* 函数要简短，一个函数只做一件事

* 函数内部局部变量不要超过5 ~ 10个，否则你需要把函数切割成更小的函数

* 源码中的函数用一个空行分隔

## 7. 集中函数的退出

* 使用**goto**集中函数的退出
**goto**的标签名可以设置为**out_free_buffer**，避免使用**err1:**和**err2:**的标签名

## 8. 注释

* 不要注释怎么做，而是注释做了什么

* 首选注释风格是：
```c
/*
 * This is the preferred style for multi-line
 * comments in the Linux kernel source code.
 * Please use it consistently.
 *
 * Description:  A column of asterisks on the left side,
 * with beginning and ending almost-blank lines.
 */
```

## 11. 数据结构

## 12. 宏，枚举和RTL

## 14. 分配内存

[1]: https://www.kernel.org/doc/Documentation/process/coding-style.rst
