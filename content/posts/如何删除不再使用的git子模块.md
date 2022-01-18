---
title: "如何删除不再使用的git子模块"
date: 2022-01-19T03:32:32+08:00
tags:
  - git
categories:
  - git
---

使用 git 的时候，有时候添加的子模块（submodule）不再需要了，这时候就可以将其删除。典型例子就是 hugo 博客的主题，一般都是以子模块的形式引入的，一旦更换新主题，旧的就不再需要了。

删除方法其实也很简单。首先反注册子模块。

```sh
git submodule deinit -f path/to/submodule
```

然后删除`.git`文件夹下隐藏的子模块信息。

```sh
rm -rf .git/modules/path/to/submodule
```

最后就可以安全的删除子模块目录里的文件了。

```sh
git rm -f path/to/submodule
```
