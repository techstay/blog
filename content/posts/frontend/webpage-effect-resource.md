---
title: "网页效果资源推荐"
date: 2022-01-26T16:48:47+08:00
tags:
  - 前端
  - 资源推荐
categories:
  - 前端
---

网上看各种个人博客经常会发现一些好玩的网页效果，每一个单独写一篇文章有点浪费，所以就直接放到一篇文章里做个记录，也方便以后查阅。

## websiteasteroids，网页打飞机

废话不多说，先来看看网站地址：

<http://www.websiteasteroids.com/>

网页很简单，点击右边的红色按钮就会显示一个白色三角小飞船，通过光标键就可以控制移动，使用空格键就可以发射子弹，将沿途的所有文字打掉（按 b 可以高亮所有可以打掉的网页元素），同时在右下角显示分数。不想玩了的话，按 esc 即可关闭。如果想要恢复被打的七零八落的网页，刷新一下就好了。网页效果最好在 chrome 浏览器中运行，edge 等浏览器可能会出现移动问题。

更有意思的是，你还可以将红色按钮拖动到收藏夹，在其他网站上也可以点击游玩，完全一样的效果，没事点两下还是蛮有意思的。

原理也很简单，鼠标移动到红色按钮上即可看到它对应的点击事件，这是一段 JavaScript 代码，在网页中创建了一个脚本代码段，然后执行 URL 对应的脚本。所以如果你有一个网站，也可以直接把这段代码复制上去，就能启用一样的效果啦。正好我目前使用的 hugo 博客也能这么玩一玩，一会儿就看看怎么加上去。

```js
javascript:var%20s%20=%20document.createElement('script');s.type='text/javascript';document.body.appendChild(s);s.src='http://www.websiteasteroids.com/asteroids.min.js';void(0);
```

## 气球爆炸

这个效果是看[米米的博客](https://zhangshuqiao.org/)得来的，鼠标点击任意位置即可展现一个气球爆炸的效果，不过虽然看起来像气球爆炸，不过文件名字却是`fireworks.js`，我按照这个名字甚至又找到了一个更加名副其实的放烟花的效果。这个效果比较简单，就是一段 js 代码，加到网页里面就行了，源代码地址<https://zhangshuqiao.org/lib/fireworks.js>。

## fireworks.js，放烟花

这是我按照上面文件名搜出来的[放烟花效果](https://fireworks.js.org)，点击链接即可查看效果。官方文档比较详细，就不用过多介绍了。

## canvas-nest，多边形网

[canvas-nest](https://github.com/hustcc/canvas-nest.js) 也是一个非常经典的网页效果，开启后可以在网页显示不断变化的多边形网的效果，并且可以跟着鼠标移动而发生变化。
