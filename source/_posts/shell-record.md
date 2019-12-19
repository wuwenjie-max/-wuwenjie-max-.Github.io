---
title: shell record
date: 2019-12-18 14:45:09
tags:
---
LINUX 常用命令记录
1： ps -e -o ppid,stat,user |grep S |grep user |cut -c 1-5 |xargs kill -9 [清除sleep进程]
2： sed -i 's/old/new/g' */*/*.sh  [替换指定文件中的某些字符串]



待续