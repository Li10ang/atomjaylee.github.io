---
title: '''禁止微信webview调整字体大小'''
date: 2016-09-05 15:42:33
categories: mobile
tags:
  - mobile
  - 移动端
---

### 往常我们写的页面如果在微信中手动调节了字体了大小，那就:sweat_smile:了

- 微信中内置了调节字体大小的功能![调节字体的大小](http://o9z96lbmh.bkt.clouddn.com/resize_font.png)

一调节就会让页面的布局出错。

<!-- more -->

- 解决方案：
	* iOS 版的调整字体大小使用的是通过给 body 设置 -webkit-text-size-adjust:120% 属性实现的

``` css
body {
-webkit-text-size-adjust: 100% !important;
}		
```

* Android 则是通过 Java 调用 webview 的 API 设置字体大小，需要通过 WeixinJSBridge 对象将网页的字体大小设置为默认大小，并且重写设置字体大小的方法，让用户不能在该网页下设置字体大小。

``` javascript
(function() {
if (typeof WeixinJSBridge == "object" && typeof WeixinJSBridge.invoke == "function") {
		handleFontSize();
} else {
		if (document.addEventListener) {
				document.addEventListener("WeixinJSBridgeReady", handleFontSize, false);
		} else if (document.attachEvent) {
				document.attachEvent("WeixinJSBridgeReady", handleFontSize);
				document.attachEvent("onWeixinJSBridgeReady", handleFontSize);
		}
}
function handleFontSize() {
		// 设置网页字体为默认大小
		WeixinJSBridge.invoke('setFontSizeCallback', { 'fontSize' : 0 });
		// 重写设置网页字体大小的事件
		WeixinJSBridge.on('menu:setfont', function() {
				WeixinJSBridge.invoke('setFontSizeCallback', { 'fontSize' : 0 });
		});
}
})();
```

> 注意：安卓下如用户之前已经设置过字体大小，本方法会先按照用户设置的大小显示，然后再跳转回正常的样式

![gif](http://o9z96lbmh.bkt.clouddn.com/resize_font_android.gif)
