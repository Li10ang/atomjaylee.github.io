---
title: github部署网站
date: 2016-09-26 13:46:49
categories: 日常折腾
tags:  
  - github
---


> 将自己开发的网站部署到网络上，不仅能够方便快捷的查看，还能提升自己的逼格，哈哈。之前我一直使用百度开放云来部署自己的网站，以便于在应聘的时候能派的上用场，但是他是收费平台，平均一天3毛左右，虽然不多，但是时间一长也是一笔不小的开支

之前的在博客中也使用'github'+'Hexo'来开发了自己的博客，那么今天也利用github来部署一下自己开发的一些小项目

<!-- more -->

1. 在自己的github中新建有一个库，名字随意
2. 点击'setting'--GitHub Pages选项中点击'Lanunch automatic generator'--填写项目的名字--点击'Continue to layouts'--进入主题选择页面，直接选择'Publish page'--返回setting，GitHub Pages选项中的'Source',默认是gh-pages,切换到master分支
3. 然后上传自己的静态资源(里面必须有index.html)，访问'Username.github.io/库的名字',就能访问到了。

> 只能部署静态资源的页面，动态资源的网站还是乖乖的使用百度开放云或者阿里云等系列的平台吧
