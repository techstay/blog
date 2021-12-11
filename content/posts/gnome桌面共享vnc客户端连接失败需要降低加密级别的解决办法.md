---
title: "gnome桌面共享vnc客户端连接失败需要降低加密级别的解决办法"
date: 2018-10-15T00:37:09+08:00
tags:
  - 疑难杂症
categories:
  - linux
---

由于一些 Windows VNC 客户端（例如 RealVNC、TightVNC 等）不支持 Gnome 桌面 Vino 服务端的加密，所以会出现这种错误。解决办法是打开 dconf 编辑器，在 org->gnome->desktop->remote-access 上，关闭 require-encryption 选项。

之后再次连接，可以发现这时候就可以连接到 Linux 桌面啦！

![dconf编辑器](/img/dconf-editor.png)
