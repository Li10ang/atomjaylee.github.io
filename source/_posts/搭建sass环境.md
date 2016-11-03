---
title: 搭建Sass环境
date: 2016-08-09 16:00:00
categories: Sass
tags:
  - sass
  - gulp
  - webpack
---
#### 网络上关于sass的使用教程很多，包括环境的搭建和语法以及相关技巧，比如阮一峰老师的[Sass用法指南](http://www.ruanyifeng.com/blog/2012/06/sass.html)和大漠老师的[十分钟入门](http://www.w3cplus.com/sassguide/)

> 听说，下雨天(Sass)和巧克力(gulp,webpack)更配哦!!!

作为一个前端的小白，也已然知道规范化，模块化，工程化和组件化是大势所趋，gulp和webpack作为工程化构建最流行的工具，也需要你花大把的时间去折腾。如果不依赖gulp或webpack等工具去搭建Sass的预编译环境还是比较麻烦的，比如window系统下你需要安装ruby再安装Sass等。  

而我们需要的是当我们编写完sass代码后，保存==编译，这就需要自动构建工具了，下面针对gulp和webpack两个工具进行简单环境配置。

<!-- more -->

1. gulp
>gulp环境下需要利用npm包管理来安装三个模块分别是gulp,gulp-sass和node-sass(*特别说明：安装node-sass可能会报错，是因为国内网络的原因，需要使用[淘宝镜像](https://npm.taobao.org)的cnpm来安装*)

简单配置如下：
``` js
var gulp = require('gulp'),//引入gulp
    sass = require('gulp-sass')//引入编译sass文件的模块

/*建立任务*/
gulp.task('sass',function(){
  return gulp.src('./sass/*.scss')//存放scss文件的地址
  .pipe(sass().on('error', sass.logError)))//防止因为编写错误而停到watch任务
  .pipe(gulp.dest('./dist/css'))//存放编译的文件
})

/*监听sass文件*/
gulp.task('watch',function(){
  gulp.watch('./sass/*.scss',['sass'])
})
/*默认开启功能*/
gulp.task('default',['sass','watch'])
```
此时命令行进入该文件夹，执行`gulp`即可开启对scss文件的编译工作

2. webpack
>webpack作为最火的模块加载器(打包)，更是方便快捷！！需要安装webpack,sass-loader,css-loader,style-loader和node-sass(*同gulp安装node-sass相同*)

简单配置如下：
``` js
var path = require('path')
var config = {
  entry:'./main.js',//入口文件
  output:{
    path:path.join(__dirname,'dist'),
    filename:'bundle.js'//输出文件
  },
  module:{
    loaders:[{test:/\.scss/,loader:'style!css!sass'}]
  }
}
module.exports = config;
```
和gulp不同，这样实现后css会以`<style>...</style>`标签的方式，将样式引入到HTML中，如果你也希望像gulp一样，也能单独成为一个文件需要安装`npm install extract-text-webpack-plugin --save-dev`插件来实现。

>所以如果你不是模块化的开发，还是使用gulp来编译，明了易懂。如果是模块化开发，webpack当仁不让
