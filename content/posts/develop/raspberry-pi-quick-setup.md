---
title: "树莓派3B+快速上手"
date: 2022-02-04T16:22:09+08:00
tags:
  - linux
  - raspberrypi
categories:
  - dev
---

最近又把吃灰的树莓派 3B+拉出来更新一下，简单记录一下。

## 安装烧录器

官方新推出了图形界面的烧录器，支持多种系统，推荐直接下载安装这个[烧录器](https://www.raspberrypi.com/software/)。

## 安装系统

从烧录器中就可以选择各种系统了，如果你手头没有多余的键盘鼠标显示器，推荐先从官方的系统开始，可以预先设置 SSH 登录和 WIFI 登录，系统安装好之后就可以直接远程连接。我这里选择了 64 位的树莓派 OS 开始安装，安装之前别忘了使用右下角的齿轮图标进行设置，安装完成后会自动弹出 SD 卡。

## 系统配置

开机之后，稍等片刻，树莓派就连接到了 WIFI，然后就可以使用 SSH 登录。推荐先使用`raspi-config`设置。最好先在接口选项里将 VNC 打开，这样以后就可以用 VNC 方式登录图形界面了。

```sh
sudo raspi-config
```

然后需要安装[RealVNC](https://www.realvnc.com/en/connect/download/viewer/)，接下来就可以使用 VNC 登录了。登录完成之后最好点击开始菜单，然后用图形化的`Raspberry Pi Configuration`继续进行配置，例如修改分辨率、修改登录密码等。

如果你喜欢温度插件，也可以右击任务栏，并在面板中添加温度显示插件，然后将其移动到合适的位置。

树莓派关机的时候和电脑一样，记得先关机在拔电源。
