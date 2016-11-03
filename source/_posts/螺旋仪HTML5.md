---
title: "'螺旋仪HTML5'"
date: 2016-09-20T14:29:37.000Z
categories: mobile 日常折腾
tags:
  - 移动端
  - HTML5
---

> 之前的淘宝造物节的AR效果让人为之惊叹，最近看见大漠前辈在微信公众号上推送了两篇关于陀螺仪相关的文章，所以写一下读后感

陀螺仪的使用是调用了HTML5的orientation,用来检测只能设备的运动方向，在移动端开发中能给用户带来良好的体验(控制游戏，手势识别，地图)； **兼容性**：移动设备现在无非是IOS和安卓系统，wp系统其实不是太常见，IOS系统>=7.1;Android>=4.0;兼容性还是相当不错的。

<!-- more -->

**坐标系**：即笛卡尔坐标系，包括有，x(aplha),y(beta),z(gamma)三个坐标系， ![](http://o9z96lbmh.bkt.clouddn.com/DeviceOrientation-4.png); aplha:数值0到360度；beta:-180到180度；gamma：-90到90度；

**使用方法**：使用方法和onclick时间相同，需要先测试一下设备是否已经支持orientation

```javascript
if (window.DeviceOrientationEvent) {
  //  支持DeviceOrientation API写在这里
} else {
  console.log("对不起，您的浏览器还不支持Device Orientation!!!");
}
```

**实例**

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Alpha & Beta & Gamma</title>
    <meta name="viewport" content="width=device-width,minimum-scale=1,maximum-scale=1">
    <style type="text/css" media="screen">
    html,
    body {
        margin: 0;
        padding: 0;
        width: 100vw;
        height: 100vh;
    }
    #myCanvas {
        margin: 20px auto;
        position: absolute;
        top: 50%;
        left: 50%;
        -webkit-transform: translate3d(-50%, -50%, 0);
        transform: translate3d(-50%, -50%, 0);
    }
    </style>
</head>
<body>
    <canvas id="myCanvas" width="360" height="450" style="border:1px solid #d3d3d3;">
    </canvas>
    <script>
    function deviceOrientationListener(event) {
        var c = document.getElementById("myCanvas");
        var ctx = c.getContext("2d");
        ctx.clearRect(0, 0, c.width, c.height);
        ctx.fillStyle = "#FF7777";
        ctx.font = "14px Verdana";
        ctx.fillText("Alpha:" + Math.round(event.alpha), 10, 20);
        ctx.beginPath();
        ctx.moveTo(180, 75);
        ctx.lineTo(210, 75);
        ctx.arc(180, 75, 60, 0, event.alpha * Math.PI / 180);
        ctx.fill();

        ctx.fillStyle = "#FF6600";
        ctx.fillText("Beta:" + Math.round(event.beta), 10, 140);
        ctx.beginPath();
        ctx.fillRect(180, 150, event.beta, 90);

        ctx.fillStyle = "#FF0000";
        ctx.fillText("Gamma:" + Math.round(event.gamma), 10, 270);
        ctx.beginPath();
        ctx.fillRect(90, 340, 180, event.gamma);
    }
    if (window.DeviceOrientationEvent) {
        window.addEventListener("deviceorientation", deviceOrientationListener);
    } else {
        alert("Sorry, your browser doesn't support Device Orientation");
    }
    </script>
</body>
</html>

```
也可以扫描下面的二维码在手机上实时查看
![png](http://o9z96lbmh.bkt.clouddn.com/DeviceOrientation-10.png)


这里特别推荐一下淘宝造物节作者的github[地址](https://github.com/shrekshrek?tab=overview&from=2016-08-01&to=2016-08-31&utf8=✓);
