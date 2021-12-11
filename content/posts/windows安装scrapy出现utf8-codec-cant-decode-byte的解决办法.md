---
title: "windows安装scrapy出现utf-8 codec can't decode byte的解决办法"
date: 2017-12-03T18:24:07+08:00
tags:
  - 疑难杂症
categories:
  - python
---

这种情况是由于 scrapy 的 python 包是针对 linux 编写的，而 windows 下的 Powershell 终端编码并不是 UTF-8，所以出现了这个编码错误。解决办法就是用支持 UTF-8 的终端，例如 Git Bash 来运行`pip install scrapy`命令。
