---
layout: post
title:  "Linux命令"
date:   2018-05-14 15:32:01 +0800
categories: Linux
---

# 文本处理

## grep

* TO DO

## sed

* TO DO

## awk

* TO DO

## wc

* TO DO

## sort

 * [sort.c](https://github.com/coreutils/coreutils/blob/master/src/sort.c)

* TO DO

## uniq

* TO DO

## seq

* TO DO

## paste

* TO DO

## join

* TO DO

# 包管理

## dpkg,rpm

||rpm |	dpkg 
|-|-|-
|安装|`rpm -i pkgfile.rpm` |`dpkg -i pkgfile.deb`
|已安装软件列表|`rpm -qa`|`dpkg -l `
|软件的文件列表|`rpm -ql softwarename`|`dpkg -L softwarename`
|移除|	`rpm -e softwarename`|`dpkg -r softwarename` (保留配置)<br/> `dpkg -P softwarename` (完全移除)
  
  
## apt-get,yum

* TO DO

## 参考
http://www.cnblogs.com/zhangfeionline/p/5893748.html

# 防火墙

## iptables
* TO DO
## firewall-cmd
* TO DO
## 参考
https://www.cnblogs.com/eaglezb/p/6073739.html


# 系统管理

## 启动方式

* 控制台启动 

    `sudo systemctl set-default multi-user.target` 

* 图形界面启动

    `sudo systemctl set-default graphical.target` 

## 服务管理
* TO DO
### 开机启动

<code>sudo systemctl enable *service_name*</code>  


## 显示

### GUI显示

* [HiDPI (简体中文) - ArchWiki](https://wiki.archlinux.org/index.php/HiDPI_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

### 控制台显示

#### 修改分辨率

`vim /etc/default/grub`

加入以下内容
```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_GFXMODE=1600x1200x32
GRUB_GFXPAYLOAD_LINUX=keep
```
```
update-grub
reboot
```
##### 参考

* [command line - Maximum terminal resolution in ubuntu server virtual box guest - Ask Ubuntu](https://askubuntu.com/q/456527) 
* [How to use ubuntu server full screen in virtualbox? - Ask Ubuntu](https://askubuntu.com/q/128309)

#### 修改字体

`vim /etc/default/console-setup`

```
FONTSIZE=16x32
```
##### 参考

* [console - Can I change the font of terminal? - Unix & Linux Stack Exchange](https://unix.stackexchange.com/q/49779)






