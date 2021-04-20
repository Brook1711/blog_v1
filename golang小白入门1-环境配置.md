---
title: golang小白入门1 环境配置
date: 2021-02-11 10:11:31
tags: [golang, beginners]
categories:
    - coding
    - golang
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/go_index.jpg
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/golang-hacker (1).jpg
---

# golang小白入门1

摘要：环境搭建（m1 mac air）；IDE（jetbrain golang）；最终目标为web开发

## 1.1、golang安装包

截至2021年2月11日，golang稳定版仍未支持

![image-20210211121740020](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211121740020.png)

请注意，目前只有go1.16rc1非稳定版支持m1 mac

下载之后一路默认安装即可。

## 1.2 jetbrains golang IDE

登陆jetbrain官网找到golangIDE

链接:

https://www.jetbrains.com/go/

下载安装一路默认，目前goland支持m1芯片，注意下载时选对架构：

![image-20210211122130216](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211122130216.png)

下载安装一路默认。

## 1.3 golang环境变量配置

在macOS中共有四个可选的终端配置文件(主目录～下，没有的话自己创建一个即可)：

- .bashrc
- .bash_profile
- .profile
- .zshrc

在任意一个文件里编辑都有相同的效果，这里以`.zshrc`文件为例：

```bash
export GOROOT=/usr/local/go
export GOPATH=/Users/guoxufeng/go
export GOBIN=$GOROOT/bin
export PATH=$PATH:$GOBIN
```

之后在主目录～的终端下执行：

```bash
source .zshrc
```

来执行刷新文件的命令，以后就可以在终端里的任意位置执行go命令。

## 1.4 goland IDE配置

![image-20210211122839397](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211122839397.png)

点击配置

在gopath中配置项目目录：

![image-20210211123009882](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211123009882.png)

这里要注意新建go语言项目的时候推荐直接在`GOPATH/src`下新建项目。如果提示没有权限那就手动在`GOPATH/src`下新建对应文件夹即可。

## 1.5 教程推荐

在知乎上转了转，目前比较全的golang教程链接如下：

https://github.com/rubyhan1314/Golang-100-Days

但是最新更新也是一年以前，如果大家有比较新的免费教程，请在评论区留言。

当然，golang官方教程也是很推荐的。