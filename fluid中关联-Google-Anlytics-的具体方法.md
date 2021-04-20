---
title: Hexo fluid 中关联 Google Anlytics 的具体方法
date: 2020-12-17 22:10:24
tags: [Hexo, Fluid, Google Anlytics]
categories:
    - coding
    - blog
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201217222314.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201217222524.png
---

# 相关链接
[我的个人博客](https://brook1711.com/2020/12/17/fluid%E4%B8%AD%E5%85%B3%E8%81%94-Google-Anlytics-%E7%9A%84%E5%85%B7%E4%BD%93%E6%96%B9%E6%B3%95/)
[我的知乎](https://zhuanlan.zhihu.com/p/338903685)
[我的CSDN](https://blog.csdn.net/weixin_42242398/article/details/111573933)

# 最终效果

![](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201217222130.png)

同时在安卓和ios端也有客户端软件，非常的方便

自己的博客总是要有查看访问量和访客情况的需求，由于我的博客是基于Hexo fluid的主题，该主题有绑定Google analytics的接口，Google analytics是比较好用的网页数据可视化工具，你可以看到访客的访问地理分布、时间分布等等

## 1、注册Google analytics 账号

（在自己的google 账号中将语言设置尽可能改成英文，方便查找外网资料）

{% btn https://analytics.google.com/analytics/web/#/, Google analytics, Google analytics 网址 %}

## 2、根据图示一步步往下走

![](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201217223158.png)

创建数据流业务的时候一定**注意**！！！！！

勾选UA服务

![image-20201217224042636](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217224042636.png)

![image-20201217223418798](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217223418798.png)

![image-20201217223513965](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217223513965.png)

然后蓝色按钮创建

![image-20201217223606076](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217223606076.png)

![image-20201217223731930](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217223731930.png)

![image-20201217224157471](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217224157471.png)

## 3、更改fluid代码设置：

在配置文件`_config.fluid.yml`中更改以下设置：

关于fluid主题的配置可参见其[官方文档](https://hexo.fluid-dev.com/docs/guide/#%E6%96%87%E7%AB%A0%E6%91%98%E8%A6%81)

enable 改为 true

google 改为 tracking ID

gtag 改为 MEASUREMENT ID

```yml
web_analytics:  # 网页访问统计
  enable: true

  # 百度统计的 Key，值需要获取下方链接中 `hm.js?` 后边的字符串
  # Baidu analytics, get the string behind `hm.js?`
  # See: https://tongji.baidu.com/sc-web/10000033910/home/site/getjs?siteId=13751376
  baidu:

  # Google 统计的 Tracking ID
  # Google analytics, set Tracking ID
  # See: https://developers.google.com/analytics/devguides/collection/analyticsjs
  google: UA-xxxxxx-1

  # Google gtag.js 的媒体资源 ID
  # Google gtag.js GA_MEASUREMENT_ID
  # See: https://developers.google.com/analytics/devguides/collection/gtagjs/
  gtag: G-xxxxxx

  # 腾讯统计的 H5 App ID，开启高级功能才有cid
  # Tencent analytics, set APP ID
  # See: https://mta.qq.com/h5/manage/ctr_app_manage
  tencent:
    sid:
    cid:

  # 51.la 站点统计 ID
  # 51.la analytics
  # See: https://www.51.la/user/site/index
  woyaola:  # 51.la 站点统计 ID，参见

  # 友盟/cnzz 站点统计 web_id
  # cnzz analytics
  # See: https://web.umeng.com/main.php?c=site&a=show
  cnzz:

  # LeanCloud 计数统计，可用于 PV UV 展示，如果 `web_analytics: enable` 没有开启，PV UV 展示只会查询不会增加
  # LeanCloud count statistics, which can be used for PV UV display. If `web_analytics: enable` is false, PV UV display will only query and not increase

```

## 4、验证效果

进入控制台中的数据流概览：

![image-20201217224601115](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201217224601115.png)

最终可以看到结果