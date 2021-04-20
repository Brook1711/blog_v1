---
title: Hexo 插件，介绍本博客使用插件
date: 2020-12-18 21:33:40
tags: [Hexo, Fluid, plug]
categories:
    - coding
    - blog
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201218213549.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/20201218213818.png
---
盘点本博客使用的插件

# 1、加密文章或页面

{% btn https://github.com/D0n9X1n/hexo-blog-encrypt, hexo-blog-encrypt, 插件GitHub仓库地址 %}

加入方法

```bash
npm install --save hexo-blog-encrypt
```

输入命令行直接安装包

使用时直接在`/source/_post/*.md`文件头部加入：

```markdown
---
title: Hello World
date: 2016-03-30 21:18:02
password: mikemessi
abstract: Here's something encrypted, password is required to continue reading.
message: Hey, password is required here.
wrong_pass_message: Oh, this is an invalid password. Check and try again, please.
wrong_hash_message: Oh, these decrypted content cannot be verified, but you can still have a look.
---
```

password字段即为加密该post页面的密码

abstract为出入密码框中的默认字段

wrong_pass_message和wrong_hash_message字段为错误提示字段

最终效果：

![image-20201218214642666](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20201218214642666.png)



# 2、看板娘

{% btn https://github.com/EYHN/hexo-helper-live2d/blob/master/README.zh-CN.md, hexo-helper-live2d, 插件GitHub仓库地址 %}

加入方法：（具体方法在上面👆的链接中）

```bash
npm install --save hexo-helper-live2d
```

首先安装包

在`/_config.fluid.yml`或`/_config.yml`中添加以下设置：

在这里我配置的是`/_config.yml`

```yml
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-wanko
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
  react:
    opacity: 0.7
```

除了有看板娘这一模板之外，还有很多好看的models供你选择

{% btn https://github.com/xiazeyu/live2d-widget-models, live2d-widget-models, model 仓库 GitHub仓库地址 %}

目前仓库中有如下的模型。

更换模型只需要更改上述代码块中的如下字段：

```yml
live2d:
  model:
    use: live2d-widget-model-wanko
```

https://huaji8.top/post/live2d-plugin-2.0/

{% btn https://huaji8.top/post/live2d-plugin-2.0/, 各插件预览图, 预览图展示地址地址 %}

> - `live2d-widget-model-chitose`
> - `live2d-widget-model-epsilon2_1`
> - `live2d-widget-model-gf`
> - `live2d-widget-model-haru/01` (use `npm install --save live2d-widget-model-haru`)
> - `live2d-widget-model-haru/02` (use `npm install --save live2d-widget-model-haru`)
> - `live2d-widget-model-haruto`
> - `live2d-widget-model-hibiki`
> - `live2d-widget-model-hijiki`
> - `live2d-widget-model-izumi`
> - `live2d-widget-model-koharu`
> - `live2d-widget-model-miku`
> - `live2d-widget-model-ni-j`
> - `live2d-widget-model-nico`
> - `live2d-widget-model-nietzsche`
> - `live2d-widget-model-nipsilon`
> - `live2d-widget-model-nito`
> - `live2d-widget-model-shizuku`
> - `live2d-widget-model-tororo`
> - `live2d-widget-model-tsumiki`
> - `live2d-widget-model-unitychan`
> - `live2d-widget-model-wanko`
> - `live2d-widget-model-z16`

效果预览：

请见本博客右下角的可爱宝宝

:)