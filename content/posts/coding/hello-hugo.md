---
title: 'Hello Hugo'
date: 2020-03-21
tags: [折腾]
toc: true
---

哈喽，🐯🐶！（开机声～）

主站顺利切换到 [Hugo](https://gohugo.io/)  

<!--more-->

### 迁移采坑记

#### 文章摘要失效

原来文章 `more` 标签像中间有空格就无效 `<!--  more  -->` 批量替换成  `<!--more-->` 解决。

#### 文章列表排序错乱

原来是文章信息的 `date` 格式不统一导致无法识别，统一修改为年月日 `date: 2020-03-21` 解决。

#### 文章内 html 标签为空

被替换为 `<!-- raw HTML omitted -->` ，原来 Hugo 0.60 以上默认禁用了，手动在 `config.toml` 添加以下代码。

```
[markup]
[markup.goldmark]
[markup.goldmark.renderer]
  unsafe = true
```

####  增加文章 TOC

新建 [layouts/partials/toc.html](https://github.com/lmm214/immmmm/blob/master/themes/hello-friend/layouts/partials/toc.html) ，修改 [layouts/_default/single.html](https://github.com/lmm214/immmmm/blob/master/themes/hello-friend/layouts/_default/single.html) 添加引用代码：

```html
    {{ if .Params.toc }}
      <div class="tocify">目录：{{- partial "toc.html" . -}}</div>
    {{ end }}
```

在文章 md 头部信息中添加 `toc: true` 启用。相关 CSS 和 jQuery 代码如下：

```css
/* tocify */
.tocify {width: 20%; max-height: 90%; overflow: auto; margin-left: 2%; position: absolute; right:2%; border-radius: 6px;}
.tocify ul, .tocify li {list-style: none; margin: 0; padding: 0; border: none; line-height: 30px; }
.tocify li a {display: inline-block; text-indent:10px; font-size: 14px; text-decoration: none; }
.tocify ul ul li a:before {content: "- "}
@media only screen and (max-width:683px) {
	.tocify {display: none;}
}
```

```js
//文章 toc 跟随
var nav = $(".tocify");
nav.removeClass("hide");
var navTop = $(".post-content").offset().top;
var w = $(window).width()/2 + 400;
nav.css("left", w);
nav.css("top", navTop);
$(window).scroll(function() {
    var scrolls = $(this).scrollTop();
    if (scrolls > navTop) {
      nav.css({"top":0,"position":"fixed"});
    } else {
      nav.css({"top":navTop,"position":"absolute"});
    };
});
```

#### 添加豆瓣页面

新建模板 [layouts/_default/books.html](https://github.com/lmm214/immmmm/blob/master/themes/hello-friend/layouts/_default/books.html) 、[layouts/_default/movies.html](https://github.com/lmm214/immmmm/blob/master/themes/hello-friend/layouts/_default/movies.html) 页面模板，自行修改 `secret`。

新建文章 [content/books.md](https://github.com/lmm214/immmmm/blob/master/content/books.md)、[content/movies.md](https://github.com/lmm214/immmmm/blob/master/content/movies.md) ，当访问 `域名/books/` 时 Hugo 会匹配 `books.html` 进行渲染。




