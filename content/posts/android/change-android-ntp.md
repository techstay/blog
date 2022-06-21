---
title: "原生安卓如何修改时间同步服务器"
date: 2021-12-05T02:28:23+08:00
tags:
  - 安卓
categories:
  - 安卓
---

本文参考自<https://zhuanlan.zhihu.com/p/32518769>。

原生安卓系统在使用的时候，有可能出现时间无法同步的问题，这是因为系统默认的时间同步服务器是`time.android.com`，咱们这儿不一定能用。所以为了正常同步时间，就要对时间同步服务器进行修改。

修改方法也很简单，启用手机的 adb 调试功能，然后在电脑使用以下命令即可。这样会将手机的时间同步服务器设为中国科学院国家授时中心，如果没有自动对时，可以手动在手机里开关一下网络对时的按钮。

```sh
adb shell "settings put global ntp_server ntp.ntsc.ac.cn"
```

当然国家授时中心的 NTP 服务器也可以在 windows 或者 linux 系统下使用。如果是 windows 系统需要在管理员权限的 Powershell 中运行下面的命令。

```powershell
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers" -Name "0" -Value "ntp.ntsc.ac.cn" -Type "String"
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers" -Name "(default)" -Value 0
```

如果是 linux 系统就运行以下命令。

```sh
sudo ntpdate ntp.ntsc.ac.cn
```