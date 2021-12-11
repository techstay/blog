---
title: "Github Desktop cannot run gpg: No such file or directory 的解决办法"
date: 2020-01-21T02:11:54+08:00
tags:
  - 疑难杂症
categories:
  - 疑难杂症
---

给 Git 配置了 gpg 密钥验证之后，使用 Github 桌面客户端的时候却出现了如题的错误。其实解决办法也很简单，因为虽然 Git Bash 自带了 gpg 工具，但是 Github Desktop 却不知道啊，所以解决办法很简单，在配置文件里写一下告诉 Github 客户端就好了。

在 Git Bash 中运行下面命令即可：

```bash
git config --global gpg.program $(which gpg)
```
