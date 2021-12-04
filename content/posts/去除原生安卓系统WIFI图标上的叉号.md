---
title: "去除原生安卓系统WIFI图标上的叉号"
date: 2021-12-04T00:44:06+08:00
tags:
 - 疑难杂症
 - 安卓
categories:
 - 安卓
---

为手机刷了LineageOS等类原生安卓系统的朋友，应该会发现在WIFI图标上可能会出现一个叉号，即使我们已经连接到了正常的网络。其实安卓系统内置了网络检测功能，会去访问谷歌家的一个网址`http://developers.google.com/generate_204`，但是因为谷歌退出了中国，所以他家的网站我们访问不了，因此就会出现这个叉号标志。

其实解决办法也很简单，虽然谷歌的网站让墙了，但是它还是有着中国官网的，所以只要我们把内部检测网址修改成国内可以访问的网站，就可以解决这个问题了。办法很简单，既然用了类原生系统，那么肯定掌握了刷机技术，那么最起码的adb命令应该是会的吧。所以我们只要打开手机的USB调试功能，将其连接到电脑上，依次输入以下命令即可：

```shell
# 查看手机连接状态
adb devices
# 进入shell模式
adb shell
# 在shell中输入以下命令
settings delete global captive_portal_http_url
settings delete global captive_portal_https_url
settings put global captive_portal_http_url http://developers.google.cn/generate_204
settings put global captive_portal_https_url https://developers.google.cn/generate_204
```

完成之后，进入再退出飞行模式，即可看到烦人的叉号已经消失了。
