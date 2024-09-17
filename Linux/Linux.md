 # 0. Linux的应用
- 网络服务器
- 金融数据库，网管环境
- 高性能计算
- 嵌入式

# 1.1 主机规划与磁盘分区
## 1.1.1 关于磁盘
 - CMOS：记录各项硬件参数并存储在主板上面的存储器
 - BIOS：开机时计算机系统会主动执行的第一个程序
	 - BIOS会一句用户的设置去取得能够开机的硬盘，且到该硬盘读取第一个扇区的MBR位置，MBR里会有基本的引导加载程序
 - MBR：主引导分区；446b
 - /c/Users/donggenhan/.ssh/id_rsa)


## 1.1.2 基础指令

- 显示日期与时间的指令： date
```
date +%Y/%m/%d
date +%H:%M
```

- 显示日历的指令： cal
- 简单好用的计算机： bc
- 惯用的关机指令： shutdown
- 重新开机，关机： reboot, halt, poweroff

## 1.1.3 按键
[TAB]：具有“命令补全”与“文件补齐”的功能

- [Tab] 接在一串指令的第一个字的后面，则为“命令补全”；
- [Tab] 接在一串指令的第二个字以后时，则为“文件补齐”！
	- 若安装 bash-completion 软件，则在某些指令后面使用 [tab] 按键时，可以进行“选项/参数的补齐”功能！

CTRL+C：中断

# 2. Linux 文件权限
- ls -al：查看文件及权限
```
[dmtsai@study ~]$ su -  # 先来切换一下身份看看
Password:
Last login: Tue Jun  2 19:32:31 CST 2015 on tty2
[root@study ~]# ls -al
total 48
dr-xr-x---.  5    root     root    4096  May 29 16:08 .
dr-xr-xr-x. 17    root     root    4096  May  4 17:56 ..
-rw-------.  1    root     root    1816  May  4 17:57 anaconda-ks.cfg
-rw-------.  1    root     root     927  Jun  2 11:27 .bash_history
-rw-r--r--.  1    root     root      18  Dec 29  2013 .bash_logout
-rw-r--r--.  1    root     root     176  Dec 29  2013 .bash_profile
-rw-r--r--.  1    root     root     176  Dec 29  2013 .bashrc
drwxr-xr-x.  3    root     root      17  May  6 00:14 .config               &lt;=范例说明处
drwx------.  3    root     root      24  May  4 17:59 .dbus
-rw-r--r--.  1    root     root    1864  May  4 18:01 initial-setup-ks.cfg  &lt;=范例说明处
[    1    ][  2 ][   3  ][  4 ][    5   ][    6     ] [       7          ]
[  权限   ][链接][拥有者][群组][文件大小][ 修改日期 ] [      文件名        ]

dr-xr-x---.  5    root     root    4096  May 29 16:08 .
d:文件类型，此处是目录
r-x:拥有着权限，可读不可写可执行
r-x:所属群属权限
---：其他人权限
5：链接数
root:拥有者
root:所属群属
4096：文件大小(byte)，如果文件名之前多一个“ . ”，则代表这个文件为“隐藏文件”
May 29 16:08:修改时间
```

改变文件权限：
- chgrp ：改变文件所属群组
- chown ：改变文件拥有者；
	- 使用者必须是已经存在系统中的帐号，也就是在/etc/passwd 这个文件中有纪录的使用者名称才能改变
- chmod ：改变文件的权限, SUID, SGID, SBIT等等的特性

```
[root@study ~]# chgrp users initial-setup-ks.cfg


```