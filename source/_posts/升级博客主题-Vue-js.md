---
title: 升级博客主题(Vue.js)
date: 2016-10-11 11:15:09
desc: vue-theme,hexo-theme,构建自己的hexo博客，前端博客
tags:
 - Vue主题
 - hexo-theme
---

今天在[掘金](http://gold.xitu.io/)上看到了关于[Vue官网主题](https://github.com/pinggod/hexo-theme-apollo)的`Hexo-theme`，所以一到公司就上手试一下，替换掉之前的Next主题。顺便对这套主题文档中的使用方法做一下实验。
<!-- more -->
# 安装
安装本主题需要的依赖包：`npm install --save hexo-renderer-jade hexo-generator-feed hexo-generator-sitemap hexo-browsersync hexo-generator-archive`  
之后执行`git clone https://github.com/pinggod/hexo-theme-apollo.git themes/apollo`将主题克隆到theme文件夹中
然后修改`_config.yml`的`theme`配置项为`apollo`，再进入`cd themes/apollo`执行`git pull`即可完成安装。

# 注意
1.标题部分，本主题只支持一级标题和二级标题，加n个`###`不起作用  
2.页面中可以设置mete description信息，可以加强网站SEO，有两种方式，第一是markdown文件头部添加`desc`配置，填写关键字和描述。第二种是在`scaffolds`文件中将`desc`配置到模板中  
3.文章摘要和Next主题相同，都是使用`<!--more-->`来进行注释  
4.警告块(和Vue中的一样)，需要使用div块和tip类名：
```html
<div class="tip">
    预处理器很强大，但它只是编写 CSS 的辅助工具。出于对扩展和维护等方面的考虑，在大型项目中有必要使用预处理器构建 CSS；但是对于小型项目，原生的 CSS 可能是一种更好的选择。不要肆意使用预处理器！
</div>
```
<div class="tip">
    预处理器很强大，但它只是编写 CSS 的辅助工具。出于对扩展和维护等方面的考虑，在大型项目中有必要使用预处理器构建 CSS；但是对于小型项目，原生的 CSS 可能是一种更好的选择。不要肆意使用预处理器！
</div>

掘金中还有一篇[文章](http://blog.naaln.com/2016/07/hexo-with-algolia/)是使用Algolia来给博客添加本站搜索功能，可是本主题使用jade作处理，尝试未成功！以后再做尝试。
