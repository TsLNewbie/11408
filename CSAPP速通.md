---
title: CSAPP速通
category: /小书匠/日记/2024-05
grammar_cjkRuby: true
---
内容来源：[【CSAPP-深入理解计算机系统】](https://www.bilibili.com/video/BV1cD4y1D7uR/?spm_id_from=333.337.search-card.all.click&vd_source=d1002d9c1ba92da4ba3fca4fdca6d750)作者：九曲阑干

# 第一章 计算机系统漫游
一个Hello Program的生命周期：
![](./images/1716303432503.png)

The Hello Program—— hello.c
```c
#include<stdio.h>
int main()
{
	printf("hello,world\n");
}
```

>linux> gcc -o hello hell.c

通过以上的命令，便能生成一个可执行程序——hello.

>编译过程分为四个阶段：**预处理，编译，汇编，连接**

![](./images/1716303711950.png)

预处理器——会通过#开头的代码，来修改原始程序，将内容直接插入到源程序中。——hello.i（文本文件）

编译——词法分析，语法分析，语义分析——（进行翻译）——hello.s

汇编——翻译成机器指令的文件——hello.o(可重定位目标文件)(二进制文件)

链接——hello中调用了printf的函数，printf在printf.o文件中（提前编译号的目标文件），把两个进行合并。——可执行目标文件hello

>了解这些知识是为了：



- 优化程序性能
	- while比for循环高效？
	- switch和if else怎么比较？
- 理解链接时出现的错误
- 避免安全漏洞
	-   缓冲区溢出是常见的问题。