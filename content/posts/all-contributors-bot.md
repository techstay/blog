---
title: "使用all-contributors机器人记录开源项目贡献者"
date: 2022-02-26T22:15:39+08:00
tags:
  - linux
categories:
  - programming
---

开源项目的协作十分重要，应该尊重每一个贡献者的劳动成果。[all-contributors](https://allcontributors.org) 项目提供了一个易于使用的 bot，帮助我们轻松将每个贡献者记录到项目之中。

首先安装 bot，<https://github.com/apps/allcontributors/installations/new>。

之后新开一个 issue，在里面输入以下指令就可以让 bot 自动创建 PR，将贡献者添加进来了。默认会在项目`README.md`文件中添加贡献者，所以需要该文件存在（内容可以为空）。或者如果贡献者太多的话，可以考虑将贡献者放到`CONTRIBUTORS.md`中，而在项目 README 醒目位置添加该文件的链接。

其中`<contributions>`是贡献类别，这里有详细说明<https://allcontributors.org/docs/en/emoji-key>。

```sh
@all-contributors please add @<username> for <contributions>
# 例
@all-contributors please add @techstay for example
```

推荐同时在项目中添加`CONTRIBUTING.md`或类似文件，里面介绍向项目发起贡献的方法，甚至可以将 all-contributors 的文档链接也带上。

如果需要修改 bot 配置的话，编辑 bot 添加的`.all-contributorsrc`文件即可，可以参考<https://allcontributors.org/docs/zh-cn/overview>。
