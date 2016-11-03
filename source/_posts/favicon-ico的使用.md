---
title: favicon.ico的使用
date: 2016-10-17 12:35:39
desc: web,网站图标,favicon,ico,logo
tags:
 - web
 - favicon
---

为了美观和提升企业的宣传，我们往往需要在网页的title位置，将企业的logo或者其他的象征性的图标放上去，就像这样：
![favicon](http://o9z96lbmh.bkt.clouddn.com/favicon.png)

<!-- more -->
## 部署方法
1.将favicon.icon文件放到根目录下（或者是image文件夹下）
2.在页面中在header位置添加`meta`声明
``` html
<!-- href中是favicon.ico文件的相对位置 -->
<link rel="shortcut icon" href="./img/favicon.ico" />
<link rel="bookmark" href="./img/favicon.ico" type="image/x-icon">
```
当然如果你希望使用动态的图标也可以这样：
``` html
<!-- href中是favicon.ico文件的相对位置 -->
<link rel="icon" href="./img/favicon.gif" type="image/gif">
```
3.图标的大小：普通的尺寸有16x16,32x32,64x64,128x128设置还有512x512.但是在实际的测试中，这个文件最好不要超过4K，所以选择32x32大小的，因为尺寸大了效果并不会见涨，还会影响了网站的速度
4.图标的制作，先用做出png格式的图片，然后在[http://www.easyicon.net/covert/](http://www.easyicon.net/covert/)上通过上传转换。

**网站使用ico图标后，在用户使用收藏夹收藏网页的时候，收藏夹中显示的是使用ico图标**
