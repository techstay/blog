---
title: "在windows上使用GnuPG"
date: 2022-01-19T04:55:23+08:00
tags:
  - GnuPG
  - 安全
categories:
  - 安全
---

GnuPG 是一个开源的加密和签名工具，广泛应用于各种对安全性有一定要求的场合。GnuPG 通常内置在各大 linux 发行版的软件仓库中，可以直接通过命令行方式安装。如果想要在 windows 上使用 GnuPG，可以通过 scoop 等方式安装。不过因为 windows 用户习惯使用命令行界面，所以其实 GnuPG 在 windows 安装包里内置了 KDE 界面的一个图形化 GnuPG 管理工具 Kleopatra，可以方便的帮助我们完成 GnuPG 的各种操作。

下面是 gpg4win 的下载地址，它包含了 GnuPG 和 Kleopatra 等一系列工具。安装时只需要同时选择 Kleopatra 即可。

<https://gpg4win.org/download.html>

如果你之前使用 git 自带的 gpg 创建了密钥的话，默认情况下 windows 版的 gpg 是搜索不到密钥的。因为前者默认保存位置是`~/.gnupg`，而 windows 下默认的 gpg 保存位置是`~\AppData\Roaming\gnupg\`。这时候有一个很简单的办法可以同步，那就是符号链接，在 powershell 中执行下面一行命令就可以为 gpg 创建符号链接文件夹，这样一来两个版本的 gpg 密钥就可以同步了。

```powershell
New-Item -path $home\AppData\Roaming\gnupg -ItemType SymbolicLink -Value $home\.gnupg\
```
