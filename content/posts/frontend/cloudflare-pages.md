---
title: "Cloudflare Pages使用方法"
date: 2022-07-14T19:28:16+08:00
tags:
  - 前端
categories:
  - 前端
---

之前我的博客一直使用 Github Pages，作为 Github 的网页托管服务还是蛮好用的。不过使用 Github Pages 有一个问题，就是静态文件同样也要作为仓库的一部分存储。这样久而久之仓库就会变得越来越大。这样根本一点也不优雅，所以最近我准备用 Cloudflare Pages 来替换。Cloudflare 的好处就是可访问性高，一般不容易被墙。

首先访问<https://pages.cloudflare.com>，从 Github 导入项目，项目类型选择 hugo。默认的 hugo 版本很低，需要创建环境变量`HUGO_VERSION`并指定一个较新的值，我使用当前的最新版`0.101.0`，这样就可以正常构建并发布了。访问一下，感觉比原来快多了。

接下来还需要处理自定义域名。如果使用 Github Pages 绑定了域名的话，首先清除相关设置，然后使用 Cloudflare 重新设置 DNS 解析。然后等待一段时间就行了。

以后写博客的时候直接正常提交就行了，Cloudflare Pages 会自动检测到提交情况，然后拉取代码重新部署。整个过程方便快捷。
