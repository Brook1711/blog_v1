---
title: golang官网教程1 初探
date: 2021-02-18 21:44:51
tags: [golang, beginners]
categories:
    - coding
    - golang
    - official tutorial
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/golang_official_index.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210218221334263.png
---

# golang官网教程1 初探

2021年2月16日，golang官方终于更新了1.16稳定版，终于可以适配m1 mac了

go1.16版本官方说明：

https://blog.golang.org/go1.16

## 1.1 官网基本信息

不得不说，golang作为新兴语言，其官网建设真的是清楚明白，接下来一一说明：

主要组成部分：

![image-20210218222405542](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210218222405542.png)

在顶部选项栏里分别是golang详细文档、golang功能包、go项目详情、帮助、go官方博客、go play。

### 1.1.1 document（开发者文档）

与其说是开发者文档，不如说是一张老少咸宜的说明书，深入浅出，将太过技术性的东西藏在链接里面，更多的是人性化的教程和说明。

>Go编程语言是一个开源项目，旨在提高程序员的生产力。
>
>Go富有表现力，简洁，整洁且高效。 它的并发机制使编写程序可以轻松地从多核和联网机器中获得最大收益，而其新颖的类型系统则可以实现灵活的模块化程序构造。 Go可以快速编译为机器代码，但具有垃圾回收的便利性和运行时反射的功能。 它是一种快速的，静态类型的编译语言，感觉就像是一种动态类型的解释语言。
>
>​									——golang官方说明

document的第一个模块是一个新手教程（getting started）：![image-20210218223433179](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210218223433179.png)包括如何安装go以及官网上手教程链接。

接下来是简易的开始教程，其实可以忽略，但是若是想了解go语言的编译原理可以简单看看：

![image-20210221210248220](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210221210248220.png)

大多数开发者包括笔者就是想用golang写后台，那么下面这个简单的web服务教程就必须看看，需要注意的是，该教程非常偏底层，要是想从头搭建一个后台可以看看，但是大多数情况下可以直接使用开源框架，比如gin和beego。gin更简洁高效，beego就像瑞士军刀，啥东西都有，而且因为是国人开发，有原生中文文档。

![image-20210221210646203](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210221210646203.png)

接下来有一篇专门描述go mod的使用方法的文章。关于go mod其实就是golang中专门管理包的工具，是go语言包中自带的，类似于python语言中的pip

![image-20210221210900023](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210221210900023.png)

最后就是[go语言线上教程](https://tour.golang.org/)，内容极其丰富，自带网页编译器，学习的同时可以锻炼英文水平。

![image-20210221211355024](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210221211355024.png)

接下来的部分就是比较高阶的操作

![image-20210221211757073](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210221211757073.png)

总的来说还是比较推荐那个[go语言线上教程](https://tour.golang.org/)

在reference一节中有更详细的文档分类：

![image-20210221211910758](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210221211910758.png)

信息量比想象中的要多，持续更新ying～

