---
title: TexStudio 论文排版细节
date: 2020-12-25 20:38:36
tags: [TexStudio, paper, IEEE]
categories:
    - paper
    - tool
index_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203815.png
banner_img: https://cdn.jsdelivr.net/gh/brook1711/fig_for_blog@master/img/20201224203849.png
comment: true
---

# TexStudio论文排版细节
# Figure

1、自定义图片标签

效果图：

![image-20210420224020819](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210420224020819.png)

使用命令：

注意，需要在最前面的 `\begin{document}`之前加入以下代码：

```latex
\newcommand{\figuretag}[1]{%
  \addtocounter{figure}{-1}%
  \renewcommand{\thefigure}{#1}%
}
```

在插图时使用：

```latex
\begin{figure}[ht]

	\centering
	\includegraphics[scale=0.5]{./Images/Bessel.png}
	\figuretag{1.6-1}\caption{The correlation between outdated and real-time CSI verse relative speed.}
	\label{fig:trajactory}
	\end{figure}
```

