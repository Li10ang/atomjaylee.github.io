---
title: '''vue2.0更新'''
date: 2016-10-08 15:55:07
categories: Vue.js
tags:
  - vue.js
  - Vue2.0
---

> Vue.js 2.0在近期已经发布了，相关的中文翻译正在进行中，自己在这里一边学习一边做一些总结，方便今后动作的查阅。

1. [Vue2.0中文文档](http://vuefe.cn/)
2. [Vue2.0官方原版](http://vuejs.org/guide/)
3. [Vue-router2.0中文文档](http://router.vuejs.org/zh-cn/index.html)
4. [Vuex2.0英文文档](http://vuex.vuejs.org/en/index.html)

### 指令
<!-- more -->
- `v-for`指令
  Vue1.x版本中使用的语法是`item in items`然后访问属性名和遍历索引值的时候分别使用`$key`和`$index`来获取，如下：


```html
<template lang="html">
  <ul class="box">
    <li v-for="item in items">{{$index}}:{{$key}}:{{item}}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items:{
        name:'Atomjaylee',
        age:24,
        num:'001',
        phone:'12345678901'
      }
    }
  }
}
</script>
```
在Vue2.0中不仅可以遍历数组，还可以遍历对象，当然也放弃了使用$index和$key的方式来获取遍历索引值和属性值。
1.遍历对象：语法`item in items`，`(item,key) in items`,`(item,key,index) in items`,**第二个参数：属性名；第三个参数：索引值**
```html
<template lang="html">
  <ul class="box">
    <li v-for="(item,key,index) in items">{{index}}-{{key}}-{{item}}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items:{
        name:'Atomjaylee',
        age:24,
        num:'001',
        phone:'12345678901'
      }
    }
  }
}
</script>
```
2.遍历数组：语法`item in items`和`(item,index) in items`
```html
<template lang="html">
  <ul class="box">
    <li v-for="(item,index) in items">{{index}}-{{item.name}}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items:[
        {name: '张三', num: '1111111'},
        {name: '李四', num: '2222222'},
        {name: '麻五', num: '3333333'}
      ]
    }
  }
}
</script>
```
