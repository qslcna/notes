---
layout: post
title:  "linux命令"
date:   2018-05-14 15:32:01 +0800
categories: linux
---

## dpkg、rpm 和 apt-get、yum 的区别及使用
### 安装

目的| rpm 用法|	dpkg 用法
-|-|-
安装指定套件|`rpm -i pkgfile.rpm` |`dpkg -i pkgfile.deb`

### 查询

目的|rpm 用法|	dpkg 用法
-|-|-
显示所有已安装的套件名称|`rpm -qa`|`dpkg -l `(小写L)
显示套件包含的所有档案|`rpm -ql softwarename` (小写L)|	`dpkg -L softwarename`
显示特定档案所属套件名称|`	rpm -qf /path/to/file`|	`dpkg -S /path/to/file`
查询套件档案资讯|	`rpm -qip pkgfile.rpm` (显示套件资讯) <br/> `rpm -qlp pkgfile.rpm` (小写L,显示套件内所有档案) |	`dpkg -I pkgfile.deb` (大写I )<br/> `dpkg -c pkgfile.deb`
显示指定套件是否安装|	`rpm -q softwarename` (只显示套件名称) <br/>`rpm -qi softwarename` (显示套件资讯)|	`dpkg -l softwarename` (小写L,只列出简洁资讯) <br/>`dpkg -s softwarename` (显示详细资讯)<br/> `dpkg -p softwarename` (显示详细资讯)

### 移除

目的|	rpm 用法|	dpkg 用法.
-|-|-
移除指定套件|	`rpm -e softwarename`|	`dpkg -r softwarename` (会留下套件设定档)<br/> `dpkg -P softwarename` (完全移除)

### 参考
http://www.cnblogs.com/zhangfeionline/p/5893748.html

## Firewall

### TODO

### 参考
https://www.cnblogs.com/eaglezb/p/6073739.html
