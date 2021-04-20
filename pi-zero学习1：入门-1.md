---
title: pi zero学习1：入门
date: 2021-02-26 10:04:26
tags: pi_zero
categories:
    - coding
    - pi zero
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226100542033.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226100613016.png
comment: true

---

# pi zero学习1：入门

官网教程地址：

https://projects.raspberrypi.org/en/projects/raspberry-pi-setting-up

## 1、简介

![plug in the pi](https://projects-static.raspberrypi.org/projects/raspberry-pi-setting-up/05f98c4cac11e7fc2ead84db91ff9f49dc23176c/en/images/pi-plug-in.gif)

这里的教程是针对树莓派4的板子，但是应该是与pi zero兼容。

具体参数如下

**Technical Specifications**

The Raspberry Pi Zero W extends the Pi Zero family. Launched at the end of February 2017, the Pi Zero W has all the functionality of the original Pi Zero, but comes with added connectivity, consisting of:

- 802.11 b/g/n wireless LAN
- Bluetooth 4.1
- Bluetooth Low Energy (BLE)

Like the Pi Zero, it also has:

- 1GHz, single-core CPU
- 512MB RAM
- Mini HDMI and USB On-The-Go ports
- Micro USB power
- HAT-compatible 40-pin header
- Composite video and reset headers
- CSI camera connector

## 2、使用SD卡启动

### Raspberry Pi Imager

树莓派团队开发了一款可以下载并自动安装景象到sd卡的软件，该软件可以在win、mac、linux平台上运行，其下载地位：

https://www.raspberrypi.org/downloads/



选择适合自己的操作系统

https://www.raspberrypi.org/software/operating-systems/

这里我选择的是Raspberry Pi OS Lite，就是不带桌面而且不带推荐软件，是最小系统。

打开刚才准备的Raspberry Pi Imager：

![image-20210226103914138](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210226103914138.png)

选择要烧录的镜像（就是刚刚下载的Raspberry Pi OS Lite）选择要烧录的sd卡，点击write按钮。

## 3、ssh连接

### 使用wifi+ssh链接

在SD卡中新建文件，命名为wpa_supplicant.conf，输入如下内容并保存。

在SD卡中新建文件，命名为ssh，内容为空。

### 使用usb连接线连结

https://gist.github.com/superdodd/06b91ba03899e47beb43078b27dc601e



## 4、网络配置

https://gist.github.com/superdodd/06b91ba03899e47beb43078b27dc601e

在进行配置之前需要开启root登陆

首先设置密码

```
sudo passwd root
```

启用 root 账号

```
sudo passwd --unlock root 
```

启用 root 账号登录

```
sudo nano /etc/ssh/sshd_config
```

```bash
#PermitRootLogin prohibit-password
PermitRootLogin yes
```

Ctrl + W 快捷键
搜索 PermitRootLogin prohibit-password
改为PermitRootLogin yes 并删掉#号
或者直接新建一行。

Ctrl + O 快捷键 保存

Ctrl + X 快捷键 退出 Nano 编辑器

这里使用usb连接ssh，编辑`/etc/network/interfaces`，添加以下内容：

```
  allow-hotplug usb0
  iface usb0 inet static
      address 192.168.2.2
      netmask 255.255.255.0
      gateway 192.168.2.1
```



## 5、换源

1、首先编辑 /etc/apt/sources.list 文件，没装vim之前，推荐用 nano 命令编辑。在修改之前先把源列表备份，然后再修改sources.list。命令如下：[mw_shl_code=bash,true]cp /etc/apt/sources.list /etc/apt/sources.list.bak  #备份为 sources.list.bak
nano /etc/apt/sources.list    #编辑sources.list 文件[/mw_shl_code]
进入编辑界面，删除原有的内容或者用#注释掉原来的源，添加下方的源：
[mw_shl_code=bash,true]#deb http://mirrordirector.raspbian.org/raspbian/ jessie main contrib non-free rpi
\# Uncomment line below then 'apt-get update' to enable 'apt-get source'
\#deb-src http://archive.raspbian.org/raspbian/ jessie main contrib non-free rpi
deb http://mirrors.aliyun.com/raspbian/raspbian/ jessie main contrib non-free rpi
deb-src http://mirrors.aliyun.com/raspbian/raspbian/ jessie main contrib non-free rpi[/mw_shl_code]
或其他源
[mw_shl_code=bash,true]#大连东软信息学院(北方用户)
\#deb http://mirrors.neusoft.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#deb-src http://mirrors.neusoft.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#中国科学技术大学
\#deb http://mirrors.ustc.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#deb-src http://mirrors.ustc.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#清华大学
\#deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#重庆大学(中西部用户)
\#deb http://mirrors.cqu.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi
\#deb-src http://mirrors.cqu.edu.cn/raspbian/raspbian/ wheezy main contrib non-free rpi[/mw_shl_code]
注意：镜像区别jessie或wheezy版本，软件源也对应一样。

```
deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ buster main contrib non-free rpi
```

```
sudo nano /etc/apt/sources.list.d/raspi.list
```

```
deb http://mirrors.ustc.edu.cn/archive.raspberrypi.org/debian/ stretch main ui
# Uncomment line below then 'apt-get update' to enable 'apt-get source'
#deb-src http://archive.raspberrypi.org/debian/ stretch main ui

```



## 6、备份

查询

```bash
#查询盘符
diskutil list 
# 下面图片中的dev/disk2既对应的树莓派的TF卡
```

dd命令

```bash
#使用dd进行备份，同时使用gzip将备份文件进行压缩
sudo dd if=/dev/disk4 bs=1m | gzip > ~/demo/pi_zero/back_wlan.gz
#将“/dev/rdiskx ”改成您 Micro SD 卡的所在位置， if 參數是指定資料來源 (也就是 Micro #SD 卡)   of 則是指定備份影像檔的儲存路徑與檔案名稱 
```

```bash
sudo diskutil unmount /dev/disk4s1

gzip -dc ./backupImage-pi-dashboard.gz | sudo dd of=/dev/disk4 bs=1m
```



## 7、pip安装

1.首先安装setuptools

```
sudo apt-get install -y python-pip  
sudo apt-get install -y python3-pip  
```

2.换源

~/.pip/pip.conf

```
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

## 8、配置远程桌面

在终端输入以下命令进入配置界面。

```
sudo raspi-config
```

依次操作：Interfacing Options -> VNC -> Yes。之后系统会提示你是否要安装 VNC 服务，输入 y 之后回车，等待系统自动下载安装完成，一切顺利的话 VNC 服务就启动了！

![image-20210227180642490](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227180642490.png)

![image-20210227180727613](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227180727613.png)

![image-20210227180744653](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227180744653.png)

![image-20210227201453435](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227201453435.png)

输入

```
vncserver
```

下载vnc viewer

![image-20210227201422979](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210227201422979.png)

框内输入树莓派ip地址即可连接



## 9、ip固定

若不进行ip固定，则很有可能电脑将其判定为MITM攻击，编辑电脑~/.ssh/known_hosts文件，删除重复host

在树莓派上：

```
sudo nano /etc/network/interfaces
```

在最后一行加入：

```
  allow-hotplug usb0
  iface usb0 inet static
      address 192.168.2.2
      netmask 255.255.255.0
      gateway 192.168.2.1
```

在`/etc/resolvconf.conf`中编辑：

```
nameservers=192.168.2.1
```

configure the RNDIS/Ethernet Gadget interface with the following parameters: - Configure IPV4: `Manually` - IP Address: `192.168.2.1` - Subnet Mask: `255.255.255.0` - Router: (none) - Under Advanced -> DNS, add your favorite DNS server, like `8.8.8.8` or your home router.