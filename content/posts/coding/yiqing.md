---
date: 2020-04-08
title: '疫情HTML源码'
tags: [网页]
published: true
hideInList: false
isTop: false
---

最新看到很多人发布疫情实时图html源码，根本不需要发布，也不存在含金量的（大神勿喷！）。

看到某站上面，还有很多店家用来卖30块钱（坑）。

<!--more-->

<center><img src="https://pic.thedoctor.top/pic/20200408C1FtLa.png"></center>
网上流传的代码，就是一个纯粹单独的iframe框架而已，没有任何技术和含金量可言。

直接贴出代码：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>全国新型冠状病毒实时分布图-信息来自国家及各省市地区卫健委</title>
    <meta name="keywords" content="全国新型冠状病毒实时分布图,实时疫情,武汉管控,新型冠状病毒,肺炎" />
    <meta name="description" content="成都市一颗优雅草科技有限公司全国新型冠状病毒肺炎病毒实时分布图，及时播报疫情最新进展！" />
</head>
<body style="height: 100vh;margin: 0;padding: 0;overflow: hidden;">
    <iframe id="iframe" src="https://www.youyacao.com/yiqing/" frameborder="0" width="100%" height="100%"
        allowtransparency="yes" style="overflow:hidden;margin: 0; border: none;"></iframe>  
</body>
</html>
```

**https://www.youyacao.com/yiqing/**

上面这个链接 换成丁香 就是丁香的页面

> 丁香的页面：https://3g.dxy.cn/newh5/view/pneumonia
>
> 网易的页面：http://news.163.com/special/epidemic/

简单说，你把任何 一个网址放进去都可以加载出他页面的内容，这就是iframe。

overflow:hidden;margin: 0; border: none; 这里的意思是超出的部分隐藏掉，不显示边框。

**>>>[效果](https://thedoctor.top/happylife/post/zhong-guo-jia-you/)<<<**

