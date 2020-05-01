---
title: Get Blogdown
author: ''
date: '2019-11-25'
slug: get-blogdown
categories:
  - hugo
tags:
  - hugo
---

### blogdown with rstudio

* Archlinux 2019

* 首先安装`R`和 `rstudio-desktop-git`,不要安装`rstudio-desktop-bin`，因为rstudio自带的Qt5库和系统安装的Qt5库不一致，不能输入中文。

* 因不明原因，需要配置好proxychains

* 在终端使用 `proxychains R` 启动后，在R命令下安装blogdown、hugo。

  ```
  install.packages("blogdown")
  blogdown::install_hugo()
  ```

* 然后启动rstudio（貌似不能输入中文）

* 配好好git账号、新建项目、ssh以及deploy的key，参考3.

* rstudio中新建项目：git和网站，两次新建项目，参考1.

* 第二次新建为网站，使用git项目地址，hugo主题选择用`hugo-xmin`，然后确认pull到本地文件夹。

* 修改主题配置，启用主题。

* 配置netlify，以及二级域名，也可以绑定自己的域名。

* 是哦嗯`blogdown::hugo_version()`查看本地安装的hugo版本。

* 在网站根目录新建`netlify.toml`，为了让netlify知道使用什么版本的hugo进行生成静态文件。

  ```
  [build]
        publish = "public"
        command = "hugo"
      # build a preview of the site [hugo --buildFuture]
      [context.deploy-preview]
        command = "hugo --buildFuture"
      # The default version you use for production if you don't use context
      [build.environment]
        HUGO_VERSION = "0.59.1"
      # The version you use for production
      [context.production.environment]
        HUGO_VERSION = "0.59.1"
      # you can lock a version of hugo for a deploy preview
      [context.deploy-preview.environment]
        HUGO_VERSION = "0.59.1"
      # you can lock a version of hugo for a branch-deploy (other than previews)
      [context.branch-deploy.environment]
        HUGO_VERSION = "0.59.1"
  ```

* 点Help下的Addins--Serve Site，将生成静态文件，并动态监控，实时生成。

* Rstudio-Version Control，或者次顶部的按钮，或者Ctrl+Alt+M，添加commit，push到github项目，若不能，先pull再push。

参考：

1. https://cosx.org/2018/01/build-blog-with-blogdown-hugo-netlify-github/
2. https://bookdown.org/yihui/blogdown/
3. https://help.github.com/cn/github/authenticating-to-github/connecting-to-github-with-ssh