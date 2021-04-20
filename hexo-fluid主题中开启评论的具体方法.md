---
title: hexo fluid主题中开启评论的具体方法
date: 2020-12-18 12:00:41
tags: [Hexo, Fluid, comments]
categories:
    - coding
    - blog
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201218120234.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201218120313.png
---
目标：在基于hexo的fluid主题中加入评论模块
参考fluid官方中文文档：https://hexo.fluid-dev.com/docs/guide/#%E8%AF%84%E8%AE%BA

## 1、修改**主题配置**：在根目录下的`_config.fluid.yml`文件

![image-20201218120752877](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201218120752877.png)

```yml
post:
  comments:
    enable: true
    type: gitalk
```

type中可选评论插件种类：

utterances | disqus | gitalk | valine | waline | changyan | livere | remark42 | twikoo

disqus会被墙所以我选择gitalk

选取种类之后需要对对应的插件进行设置：

```yml
gitalk:
  clientID:
  clientSecret:
  repo:
  owner:
  admin: ['name']
  language: zh-CN
  labels: ['Gitalk']
  perPage: 10
  pagerDirection: last
  distractionFreeMode: false
  createIssueManually: true
```

对应的属性之后都会修改

## 2、在github中创建应用

点击链接创建应用

https://github.com/settings/applications/new

![image-20201218122310526](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201218122310526.png)

参数说明：

> Application name： 应用名称，随意
> Homepage URL： 网站URL，对应自己博客地址
> Application description ：描述，随意
> Authorization callback URL：# 网站URL，博客地址就好

注册完成之后会看到

![image-20201218122825599](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201218122825599.png)

将ID和secret填进以下区域

```yml
gitalk:
  clientID:
  clientSecret:
  repo:
  owner:
  admin: ['name']
  language: zh-CN
  labels: ['Gitalk']
  perPage: 10
  pagerDirection: last
  distractionFreeMode: false
  createIssueManually: true
```

![image-20201218125523775](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201218125523775.png)

注意attention！！！

1、repo: 中填写的是仓库名，就是你初始化博客用的仓库

（该仓库必须**公开**！！）

2、owner 中的用户名不能有引号

3、distractionFreeMode建议开启false，必须登录GitHub才能评论

## 最终效果：

![image-20201218125838680](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201218125838680.png)

