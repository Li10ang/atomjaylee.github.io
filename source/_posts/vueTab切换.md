---
title: vueTab切换
date: 2016-10-19 10:20:11
tags:
---


学习东西只有边学边做才有效率，遇不到坑就成长不了，今天看了看[Element UI](http://element.eleme.io/#/)得文档，对他的Tab功能实践一下：
![gif](http://o9z96lbmh.bkt.clouddn.com/Vue_Tab)

<!-- more -->

``` html
<ul class="nav">
  <li v-for="(item,index) in items" v-on:click="bottomline(index)" v-bind:class="{ active: item.flag }" v-bind:index="index">{{item.name}}</li>
</ul>
```

1.Vue2.js中v-for指令的改变  
2.盒子的属性不能使用`Mustache`语法  
3.动态的class绑定需要使用v-bind来绑定  
4.将`index`作为参数，传递给点击方法

``` js
<script>
export default {
  data () {
    return {
      items:[
        { flag: 0, name: '指南'},
        { flag: 0, name: '组件'},
        { flag: 0, name: '资源'}
      ]
    }
  },
  computed: {},
  mounted () {},
  methods: {
    bottomline: function(index){
      this.items.map(function (v,i) {
        i==index? v.flag=1: v.flag=0;
    });
    }
  },
  components: {}
}
</script>
```
这里使用了`Array.map()`方法，其中`v`是当前元素的值，`i`是当期元素的索引值。然后去和传进来的index参数比较。
