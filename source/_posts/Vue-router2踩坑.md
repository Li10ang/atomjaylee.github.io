---
title: Vue-router2踩坑
date: 2016-10-11 11:59:50
desc: Vue.js2,Vue-router2,MVVM
tags:
 - Vue.js
 - Vue-router2
---

本篇文章也可以是2016-10-10的笔记，之前Vue.js2没有升级的时候曾使用过Vue-router@0.7.13版本实验过路由功能，今天再使用Vue-router2实验时各种报错，在这里说明一下
> Vue-router2只适用Vue.js2+版本，所以要在Vue.js1.x版本使用Vue-router，必须使用@0.7.13版本的，否则不适用。  
> 现在使用npm install Vue和npm install Vue-router安装时都是默认安装的2.0版本的，如果需要更改版本可以在package.json更改版本然后npm install  
> 也可以先使用`npm view packname versions`来查看这个包的版本，然后使用`npm install packname@xxx`来通过版本号安装

<!-- more -->
# 使用
按照Vue-router2的[文档](http://router.vuejs.org/zh-cn/essentials/getting-started.html)来试验，但是还是会报错，这里需要：（App.vue+main.js）
``` js
    new Vue({
      router,
      render: h => h(App) //这里需要使用render函数，否则会报错
    }).$mount('#app')
```
但是这样还是会报错：
<div class="tip">
    [Vue warn] : You are using the runtime-only build of Vue where the template option is not available. Either pre-compile the templates into render functions, or use the compiler-included build. (found in root instance)
</div>

这就懵逼了，这篇[文章](https://segmentfault.com/a/1190000006435886)给出了答案，先上图后解释：
![render](http://o9z96lbmh.bkt.clouddn.com/Vue2-template-render)

这里先说一下Vue最早会打包成三个文件，一个是 runtime only 的文件 vue.common.js，一个是 compiler only 的文件 compiler.js，一个是 runtime + compiler 的文件 vue.js。也就是说`vue.js = vue.common.js + compiler.js`,而从图中可以发现在运行时构建时是不支持`template`选项的，而要想支持template选项必须使用`compiler.js`这个文件，这时候你会发现，在使用vue-cli构建出来的build文件夹中`webpack.base.conf.js`文件中
``` js
resolve: {
    extensions: ['', '.js', '.vue'],
    fallback: [path.join(__dirname, '../node_modules')],
    alias: {
      'vue': 'vue/dist/vue.common.js', //调用的是vue.common.js,而不是Vue.js,这就比较尴尬了......
      'src': path.resolve(__dirname, '../src'),
      'assets': path.resolve(__dirname, '../src/assets'),
      'components': path.resolve(__dirname, '../src/components')
    }
  },
```

所以需要需改成：
``` js
resolve: {
    extensions: ['', '.js', '.vue'],
    fallback: [path.join(__dirname, '../node_modules')],
    alias: {
      'vue': 'vue/dist/vue.js', 
      'src': path.resolve(__dirname, '../src'),
      'assets': path.resolve(__dirname, '../src/assets'),
      'components': path.resolve(__dirname, '../src/components')
    }
  },
```
这就Ok了。追根溯源，完美！！  
当然Vue-router2([文档](http://vuefe.cn/router/))也更新了许多的东西，在这里就不说明了，后面会专门再写一篇博客，一边学习一边总结，生命不息，折腾不止，加油。