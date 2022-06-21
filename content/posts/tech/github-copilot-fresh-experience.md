---
title: "Github Copilot尝鲜体验"
date: 2022-01-27T17:55:29+08:00
tags:
  - Github
categories:
  - tech
---

Github Copilot 是 Github 出品的一款 AI 辅助代码补全工具，利用人工智能和大数据，帮助程序员们快速完成一些代码。当然，这个东西其实出来也有一段时间了，不过可惜的是，目前仍然处于内测阶段，而我也是刚刚才拿到了内测资格。虽然有点晚，但是既然能用了，那就来试试现在的人工智能究竟强到了什么程度了吧。

## 安装

安装方法很简单，在 vscode 里面直接搜索安装`Github Copilot`扩展即可。对于 Jetbrains 系 IDE 和 neovim 也有扩展可以安装。而这也是目前主流的几个编辑器环境了。安装完毕之后会提示你登录 Github 账号才能使用，只有申请通过了才能试用。

成功之后在 vscode 右下角状态栏应该就会看到 Copilot 的图标，这样就算准备就绪，可以开始享受 Copilot 的功能了。

## 快捷键

Copilot 的快捷键如下：

- `Tab`，接受建议
- `Esc`，忽略建议
- `Alt+\`，激活建议
- `Alt+[`，上一个建议
- `Alt+]`，下一个建议
- `Ctrl+Enter`，打开 Copilot 面板，展示最多 10 个代码建议

`Ctrl+Enter`默认是用来输入下一行的，所以我把 Copilot 的最后一个快捷键关闭了，防止冲突。

```json
[
  {
    "key": "ctrl+enter",
    "command": "-github.copilot.generate",
    "when": "editorTextFocus && github.copilot.activated"
  }
]
```

## 使用

Copilot 使用起来很简单，它基于 Github 上部署的海量开源代码训练而成，支持多种语言。只需要在注释中用英文编写要实现的功能，然后按`Alt+\`激活建议即可。如果代码建议和你想要的功能接近，就可以用`Tab`快捷键直接上屏。当然，目前的人工智能还不是很完善，想要替代程序员还有很长的路。不过对于一些非常常见的样板代码，Copilot 的效果非常不错。

下面就是一个简单的例子，只需要输入第一行的注释，Copilot 就可以生成下面的函数，真的非常方便。

```py
# print current time
def print_time():
    import time

    print("Current time: %s" % time.strftime("%H:%M:%S"))


print_time()
```

不过考虑到 Copilot 之前爆出了不少代码许可证和隐私相关的问题，估计要正式开放还要面临很多问题。不过假如都能合理解决的话，我相信 Copilot 必定会成为程序员们的又一大杀器。
