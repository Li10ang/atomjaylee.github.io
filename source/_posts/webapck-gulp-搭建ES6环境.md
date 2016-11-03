---
title: webapck/gulp 搭建ES6环境
date: 2016-08-16 12:20:04
categories: ES6
tags:
  - javascript
  - ES6
  - webpack
  - gulp
---

> Es6出现之后越来越多的人使用，它是对ES6的升华和查漏补缺，阮一峰老师ES6的也出了相关的教程--[《ECMAScript 6 入门》](http://es6.ruanyifeng.com)

*但是Es6的支持性并不是那么好，所以需要使用[编译器](http://babeljs.cn)编译成es5的语法*
<!-- more -->
#### **gulp**
> 条件：安装gulp,gulp-babel,babel-preset-es2015,babel-preset-stage-3/2/1

1.新建`.babelrc`文件
```js
{
  "presets": [
    "es2015",
    "stage-3"
  ],
  "plugins": []
}
```
2.gulpfile.js文件
```js
var gulp = require('gulp')
var babel = require('gulp-babel')

gulp.task('default',function(){
  return gulp.src('./main.js')
  .pipe(babel({presets: ['es2015']}))
  .pipe(gulp.dest('./dist'))
})
```
#### **webapck**
> 条件：webpack babel-loader babel-preset-es2015,babel-preset-stage-3/2/1

1.新建`.babelrc`文件
```js
{
  "presets": [
    "es2015",
    "stage-3"
  ],
  "plugins": []
}
```
2.webpack.config.js
```js
module.exports = {
  entry:'./main.js',
  output:{
    path:'./dist',
    filename:'bundle.js'
  },
  module:{
    loaders:[{test:/\.js/,loader:'babel'}]
  }
}
```
