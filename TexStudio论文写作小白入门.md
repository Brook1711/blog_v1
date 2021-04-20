---
title: TexStudio论文写作小白入门
date: 2020-12-24 19:20:51
tags: [TexStudio, paper, IEEE]
categories:
    - paper
    - tool
index_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203815.png
banner_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203849.png
comment: true

---

# 相关链接
## [我的个人博客](https://brook1711.com/2020/12/24/TexStudio%E8%AE%BA%E6%96%87%E5%86%99%E4%BD%9C%E5%B0%8F%E7%99%BD%E5%85%A5%E9%97%A8/)
## [我的CSDN](https://blog.csdn.net/weixin_42242398/article/details/111670612)
## [我的github](https://github.com/Brook1711)

# TexStudio论文写作小白入门

博主今年大四，由于直博的原因希望尽早开始写论文，作为一名小白希望把这个过程记录下来并希望对后人有所帮助。

博主专业通信工程，未来几年基本都会在IEEE电气电子工程师学会发文

## 0、下载安装TexStudio和MikTex

TexStudio下载地址

https://www.texstudio.org/

MikTex下载地址

https://miktex.org/

两个软件都是直接下载安装一路默认就可以

## 1、确定发稿类型

IEEE一般会有以下几种论文类型：

**Transactions** （学报，主要为高水平技术类文章）

IEEE Transactions on Wireless Communications (TWC)

IEEE Transactions on Communications (TCOM)

IEEE Transactions on Signal Processing (TSP) 

IEEE Transactions on Vehicular Technology (TVT)

 

（P.S.: TWC和TCOM是通信界公认的顶级期刊，TSP是信号处理界公认的顶级期刊。因为我们做RIS，所以TSP也要关注。上面所列举的Trans.类的期刊虽然都是二区，但都是公认的质量很高的期刊，比下面列举的一些journal / letter质量更高一些。所以Trans.也是我们需要重点阅读的期刊。）

 

**Journal** （期刊，技术类+综述类文章，多以技术类文章为主）

IEEE Journal on Selected Areas in Communications (JSAC)

IEEE Journal of Selected Topics in Signal Processing (JSTSP)

IEEE Internet of Things Journal (JIOT)

IEEE Systems Journal (SJ)

 

（P.S.: JSAC是需要重点关注的期刊，无论是影响因子还是文章质量，都是通信界公认的顶级期刊，内容涵盖也很广。JSTSP是信号处理类的专刊，文章质量也很高。剩下两个关注一下即可。）

 

**Letter** （快报，文章短不超过5页，特点是文章的idea很新，发表速度相比Trans.快。所以很多人先在Letter上发表一个创新点，工作可以不用那么完整，之后再在Trans.上发表详细的技术内容。）

IEEE Wireless Communications Letters (WCL)

IEEE Communications Letters (CL)

IEEE Signal Processing Letters (SPL)

 

**Magazine** （杂志，综述类文章。特点是影响因子高。面向群体为大众而非专业人员，所以公式推导较少。）

IEEE Communications Magazine

IEEE Wireless Communications

Proceedings of the IEEE

IEEE Vehicular Technology Magazine

IEEE Network

 

如果想查某个期刊的影响因子以及具体分区可以在这个网站上查找：

http://www.letpub.com.cn/index.php?page=journalapp

 

 

**相关会议**

（P.S.: **会议论文不应当作为我们的重点阅读对象****。**因为会议论文较短，即便是顶级会议录用的paper，质量也是参差不齐的，所以我们作为一个参考就行，对于文章质量的好坏应该有一个自己的评判。这里我列出一些顶级会议和权威会议，都是通信业界公认的一些会议。因为通信会议实在太多了，其他很多会议我们无需关注，只看最好的即可。）

 

GlobeCom (IEEE Global Communications Conference)

ICC (IEEE International Conference on Communications)

ICASSP (IEEE International Conference on Acoustics, Speech and Signal Processing)

SPAWC (IEEE International Workshop on Signal Processing Advances in Wireless Communications)

WCNC (IEEE Wireless Communications and Networking Conference)

PIMRC (International Symposium on Personal, Indoor and Mobile Radio Communications)

VTC (Vehicular Technology Conference)

 

（上面这几个会议GlobeCom≈ICC>WCNC≈PIMRC≈VTC；ICASSP和SPAWC是信号处理类的顶会，质量约等于ICC。）

## 2、在官网下载论文模板

模板可以在IEEE官网找到：

https://template-selector.ieee.org/secure/templateSelector/publicationType

### 2.1 选择出版物类型

我这里选择的是Letter：

![image-20201224204337680](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204337680.png)

### 2.2 选择出版物

我这里选择的是wireless communication Letters

![image-20201224204323411](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204323411.png)



### 2.3 选择文章类型

Letters只有一个选项

![image-20201224204027677](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204027677.png)

### 2.4 选择模板格式

这里选择LaTex

![image-20201224204013473](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204013473.png)

### 2.5 下载模板

全部选择完成后就可以看到你想要的下载按钮了

![image-20201224204002146](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204002146.png)

## 3、使用TexStudio打开下载的模板



在压缩包的如下路径中可以找到：

bare_jrnl.tex文件，这就是我们需要的模板

![image-20201224204506130](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204506130.png)

右键通过TexStudio打开

点击左上角编译键编译

![image-20201224204525145](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224204525145.png)

就可以看到代码实现的效果：

![image-20201224204601627](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201225121412.png)

这时文档是双栏的，但是在投稿时经常会要求单栏，那么在代码的最上方插入代码：

```latex
\documentclass[12pt, draftclsnofoot, onecolumn]{IEEEtran}
```

即可转换为单栏视图

![20201224204856.png](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224204856.png)

## 具体投稿格式（WCL）

https://www.comsoc.org/publications/journals/ieee-wcl/ieee-wireless-communications-letters-submit-manuscript

![image-20201224205317041](https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/image-20201224205317041.png)