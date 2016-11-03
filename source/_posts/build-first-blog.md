---
title: 搭建Hexo记录
date: 2016-08-04 15:12:49
categories: 日常折腾
tags:
  - Hexo
---

> 在我看来前端是一个比较繁杂的工作，这就意味着平时需要记录许多东西，俗话说“好记性不如烂笔头”，为了逼格和方便查阅，‘印象笔记’，'锤子便签'等满足不了自己的需求。

### 网上关于搭建hexo博客系很多，这里只做简单的概括
<!-- more -->
- 过程：
  1. 搭建环境：
    - 自己的github，建一个和你名字一样的库，例如:atomlaylee.github.io;
    - [node.js](http://nodejs.cn/);
    - [git](https://git-scm.com/downloads);
    - 新建hexo文件夹-文件夹中右击`Git Bash Here`-执行`hexo init`
  2. hexo 常用命令：
    ```js
    // 相当于清除缓存(public)
      hexo clean
    // 生成页面
      hexo g
    // 部署
      hexo d
    // 新建文章
      hexo new "文章的名字"
    // 新建页面
      hexo new page "页面的名字"
    // 本地预览(端口4000)
      hexo s --debug
    ```
- 踩得坑:
  1. windows系统下github中新建库不能是大小写混合的
  2. 运行hexo命令的时候不要在cmd中运行，要在git bash中运行，否则hexo d会报错，当然需要提前在bash中设置`git config --global user.email "你的邮箱"`和`git config --global user.name "你的用户名"`
  3.  _config.yml中连接github的库
    ```
    deploy:
      type: git
      repo: https://github.com/atomjaylee/atomjaylee.github.io.git
      branch: master

    ```
  4. node_module中需要安装`npm install hexo-deployer-git --save`
  5. hexo不支持emoji表情

- 主题
  - 我选用next主题，因为他的[文档](http://theme-next.iissnan.com/)健全
