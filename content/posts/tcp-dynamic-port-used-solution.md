---
title: "Windows动态端口号占用的解决办法"
date: 2022-02-23T17:05:46+08:00
tags:
  - windows
  - 网络
  - hyperv
  - 疑难杂症
categories:
  - 疑难杂症
---

如果你开启了 HyperV 功能，那么很有可能会出现莫名其妙的端口号占用问题，一些聪明的程序可能会使用随机端口号来工作，而一些比较死板的程序则会直接无法启动。当你使用 tcpview 等程序查看端口号占用情况的时候，则会发现其实这个端口号并没有被占用。而当重启之后，这个问题又会悄悄消失。

我被这个问题困扰了许久，最后终于在大佬的指点下解决了这个问题。根本原因是 Windows 的动态端口号机制，会占用一些端口号保留使用，本来这个机制保留的端口号是从 49152 开始，不会和主流应用冲突。**但是如果你开启了 HyperV，那么动态端口号就会改为从 1024 开始，那么很多常用的端口号都有可能被保留，导致依赖这些端口号的程序无法正常工作！**

知道了问题，那么解决起来就十分简单了。首先打开管理员权限的 powershell，查看一下动态端口号的范围。

```powershell
netsh interface ipv4 show dynamicport tcp
# 或者
Get-NetTCPSetting|select SettingName, DynamicPortRange*
```

如果你开启了 HyperV 的话，那么这里显示的应该会从 1024 开始，那么恭喜你中招了。解决办法很简单，重新指定一下端口号范围即可。

```powershell
netsh int ipv4 set dynamic tcp start=40000 num=10000
# 或者
Set-NetTCPSetting -DynamicPortRangeStartPort 40000 -DynamicPortRangeNumberOfPorts 10000
```

之后重启电脑，这个烦人的问题应该不会再出现了。
