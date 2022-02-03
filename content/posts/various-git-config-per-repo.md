---
title: "为多个git仓库启用不同的配置"
date: 2021-12-04T20:48:13+08:00
tags:
  - git
categories:
  - 编程
---

本文参考了[how-to-tell-git-which-private-key-to-use](https://superuser.com/questions/232373/how-to-tell-git-which-private-key-to-use)。

有时候我们需要同时在多个 git 仓库上工作，并且对每个仓库使用不同的 git 配置乃至密钥。这样做起来其实也并不困难。

首先切换到仓库目录下，在这里可以设置项目级别的 git 配置，只在当前 git 仓库中生效。

```sh
# 在仓库目录中
git config user.name user1
git config user.email user1@email.com
```

如果要用 ssh 方式提交代码，那么还需要让 git 知道如何去寻找不同的密钥。这可以通过 git 的`sshCommand`配置做到，只需要在项目级别的 git 配置里添加自定义的 ssh 命令，在命令里指定要使用的密钥。

```sh
git config core.sshCommand "ssh -i ~/.ssh/id_rsa_example -F /dev/null"
```

这样一来，我们就完成了多个 git 仓库的不同配置，它们之间互不干扰。
