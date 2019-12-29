---
title: shell record
date: 2019-12-18 14:45:09
tags:
	- shell
categories: 知识积累
preview_text: 平时常用的一些shell命令
preview: imgs/preview/preview3.jpg
---
LINUX 常用命令记录
1： ps -e -o ppid,stat,user |grep S |grep user |cut -c 1-5 |xargs kill -9 [清除sleep进程]
2： sed -i 's/old/new/g' */*/*.sh  [替换指定文件中的某些字符串]
3： grep -rn 'str' /dir/*          [查看包含str 的文件及行数]
4:  cat file.txt |awk '{if(NR==10){print}}'  [只打印file.txt文件的第十行]
5： last -n 10 |awk '{print $1}'  [前10行中只打印第一列]
6： cat /etc/passwd |awk -F ':' '{print $1}' [以':'分割 ，只看passwd文件中第一列]
7： awk 内置变量 ：
	ARGC               命令行参数个数
	ARGV               命令行参数排列
	ENVIRON            支持队列中系统环境变量的使用
	FILENAME           awk浏览的文件名
	FNR                浏览文件的记录数
	FS                 设置输入域分隔符，等价于命令行 -F选项
	NF                 浏览记录的域的个数
	NR                 已读的记录数
	OFS                输出域分隔符
	ORS                输出记录分隔符
	RS                 控制记录分隔符



待续