---
title: 基于donkey car的RC小玩具
date: 2021-03-04 20:19:52
tags: [python, donkey car]
categories:
    - playing
    - python
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210304202137121.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210304202059172.png
---

# 基于donkey car的RC小玩具

由raspberry pi zero w 运行python脚本，基于web端远程控制的RC玩具

donkeycar[官网](http://docs.donkeycar.com/)

## 1、树莓派准备

根据官网[指引](http://docs.donkeycar.com/guide/robot_sbc/setup_raspberry_pi/)

首先开启摄像头：

```
sudo raspi-config
```

进入系统设置后

![image-20210304202512847](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210304202512847.png)

选择启用以下功能

- enable `Interfacing Options` - `I2C`
- enable `Interfacing Options` - `Camera`

选择重启树莓派：

安装依赖：

```
sudo apt-get install build-essential python3 python3-dev python3-pip python3-virtualenv python3-numpy python3-picamera python3-pandas python3-rpi.gpio i2c-tools avahi-utils joystick libopenjp2-7-dev libtiff5-dev gfortran libatlas-base-dev libopenblas-dev libhdf5-serial-dev git ntp
```

这一步比较耗时，建议换源。

选择性，注意，不推荐安装（opencv）

```
sudo apt-get install libilmbase-dev libopenexr-dev libgstreamer1.0-dev libjasper-dev libwebp-dev libatlas-base-dev libavcodec-dev libavformat-dev libswscale-dev libqtgui4 libqt4-test

```

接下来官网推荐建立python虚拟环境

>Step 10: Setup Virtual Env
>
>This needs to be done only once:

```bash
python3 -m virtualenv -p python3 env --system-site-packages
echo "source env/bin/activate" >> ~/.bashrc
source ~/.bashrc
```

> Modifying your `.bashrc` in this way will automatically enable this 

这里直接在默认环境下运行。

新建`demo`文件夹，在该文件夹下从donkey car项目地址拉取项目代码：

- Create and change to a directory you would like to use as the head of your projects.

```bash
mkdir demo
cd demo
```

- Get the latest donkeycar from Github.

```bash
git clone https://github.com/autorope/donkeycar
cd donkeycar
git checkout master
pip install -e .[pi]
pip install numpy --upgrade
wget "https://raw.githubusercontent.com/PINTO0309/Tensorflow-bin/master/tensorflow-2.3.1-cp37-none-linux_armv7l_download.sh"
chmod u+x tensorflow-2.3.1-cp37-none-linux_armv7l_download.sh
tensorflow-2.3.1-cp37-none-linux_armv7l_download.sh
pip install tensorflow-2.3.1-cp37-none-linux_armv7l.whl
```

