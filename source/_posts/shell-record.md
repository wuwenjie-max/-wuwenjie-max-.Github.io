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



待续