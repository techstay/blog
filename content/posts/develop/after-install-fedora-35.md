---
title: "安装 Fedora35 之后要做的一些事"
date: 2021-12-09T04:40:56+08:00
tags:
  - linux
categories:
  - linux
---

## 用户配置

### 设置 sudo 免密码

默认情况下运行 sudo 命令需要输入当前用户的密码，不是很方便。我日常使用的时候喜欢改成免密码就可以运行速 sudo 命令，只需要运行下面的命令，就可以将当前用户设置成免密码即可执行 sudo 命令的情况，当然，执行这个命令的时候还是需要输入一次密码的。

```sh
echo "$(whoami) ALL=(ALL) NOPASSWD: ALL" | sudo tee "/etc/sudoers.d/$(whoami)"
```

### 使用 zim

很多人都是用 ohmyzsh 这个知名的 zsh 框架来获取强大的 zsh 生态，不过 ohmyzsh 太过大而全，所以又有了一些轻量级的 zsh 配置框架，例如 antigen（我很喜欢用，不过两年没更新了）、zinit（很强大的一个框架，不过配置比较复杂）、还有今天要介绍的 zim。要使用 zim，首先确保安装了 git、zsh、wget 等工具。

```sh
sudo dnf install wget zsh git
```

然后将用户的默认终端设置为 zsh。

```sh
chsh -s /bin/zsh
```

然后用下面的命令就可以安装 zim 了。

```sh
wget -nv -O - https://raw.githubusercontent.com/zimfw/install/master/install.zsh | zsh
```

zim 的优点就是拥有开箱即用的体验，你不需要配置什么就可以享受预先配置好的终端补全、提示和代码高亮。zim 主要有两个配置文件，`.zimrc`里面定义要安装的各种模块，`.zshrc`里面则是各个模块的配置以及用户自己的配置，这里列出我的配置供参考<https://github.com/techstay/dotfiles>。

## 系统美化

### 安装主题

这里采用经典的 flat-remix 主题。

```sh
sudo dnf install flat-remix-theme
```

主题安装完了需要启用，这要安装另外一个叫做优化工具的程序。

```sh
sudo dnf install gnome-tweaks
```

然后在优化工具中找到刚刚安装的 remix 系列主题，选择一个即可。

### gnome 扩展

为了安装和调整 gnome 扩展，需要安装扩展工具。

```sh
flatpak install org.gnome.Extensions
```

然后打开浏览器，安装下面两个扩展。第一次安装需要在页面上点击安装浏览器的扩展，安装完毕之后就能在网页上看到启用按钮。点击启用按钮即可自动下载并安装对应的 gnome 扩展。

- <https://extensions.gnome.org/extension/307/dash-to-dock/>
- <https://extensions.gnome.org/extension/6/applications-menu/>

然后打开扩展程序，找到 dash-to-dock 和 application-menu 两个扩展，启用即可。对于 dash-to-dock，还可以进行进一步的定制。

## 软件安装

### vscode

vscode 有两种安装方法，第一种是添加 vscode 的软件仓库。

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo sh -c 'echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/vscode.repo'
dnf check-update
sudo dnf install code
```

第二种是直接用 flatpak 安装。我个人喜欢用第二种方式安装。

```sh
flatpak install https://flathub.org/repo/appstream/com.visualstudio.code.flatpakref
```

如果用 flatpak 安装失败，提示远程 flathub 找不到软件，需要先添加一下。然后再运行上面的命令就可以顺利安装了。

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```
