---
title: "配置和美化你的powershell终端"
date: 2021-12-11T02:09:25+08:00
tags:
  - powershell
categories:
  - 编程
---

一直以来我都不太喜欢在 Powershell 下使用命令行，一个重要原因就是 Powershell 没有像 ohmyzsh 那样成熟的生态，没有各种各样强大的插件支持，其实命令行用起来并不舒服。不过最近正好看到了几个 Powershell 有关的教程，觉得挺有意思，就研究了一下，配置完成以后的 Powershell 其实用起来感觉还可以。所以就来给大家介绍一下。

## 必需软件

### powershell

Powershell 虽然已经内置在了 Windows 之中，不过系统自带的 Powershell 是 5.1 版，已经算是一个很老的版本了。所以这里推荐安装最新的 7.2 版本，这是目前最新的版本。Powershell 可以直接在微软商店中安装，不过商店版有一点点权限限制。所以你也可以直接从 Github 上下载 Powershell，<https://github.com/PowerShell/PowerShell/releases/>。

### scoop

一个简单方便的 windows 下的包管理器，优点是把软件全部安装在用户主目录下的一个文件夹中，管理和删除都非常方便。而且默认情况下不需要启用管理员权限，我们也不必每次专门开一个管理员权限的窗口来运行命令。用下面的命令就可以安装 scoop 包管理器。

```powershell
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```

### Windows Terminal

微软开发的一个现代终端软件，用来替代老旧的控制台终端。Windows Terminal 的特点是颜值高，而且已经是 Windows 11 的默认终端了，如果你还在使用 Windows 10，也可以在应用商店中安装 Windows Termial。

### Git

Git 是世界上最流行的版本控制软件，有大量项目都使用它来管理代码。这里用到的一些工具也都是由 git 管理的，所以 git 也是一个必装的软件。在安装 scoop 包管理器之后，我们可以通过 scoop 简单的安装 git。

```sh
scoop install git
```

### vscode

vscode 是一个非常流行的开源、免费的文本编辑器，拥有广泛的生态，这里我们主要使用 vscode 来编辑一些配置文件，甚至我这篇文章也是在 vscode 中编辑完成的。

## 配置 Windows Terminal

### 安装 NF 字体

后面介绍的一些功能会有显示一些特殊字符的需求，所以这里我们要提前安装一些支持特殊字符的字体。而 [nerd-fonts](https://github.com/ryanoasis/nerd-fonts) 这个项目，包含了众多适配过特殊字符的字体，可以放心使用。这里推荐`Meslo-Nerd-Fonts`，可以在 scoop 中安装。

```sh
# scoop默认没有开启nerd-fonts分类，需要开启才能安装相关字体
scoop bucket add nerd-fonts
# 安装字体时需要在管理员权限的终端中运行
scoop install Meslo-NF-Mono
```

### Windows Terminal 选项

然后再来配置一下 Windows Terminal，点击下拉菜单选择设置打开设置标签页，然后依次修改以下选项：

- 启动->默认配置文件，改为 Powershell，如果你已经安装了 Powershell 7.2，这里应当可以自动搜索到。否则可能需要手动编辑配置文件。
- 启动->默认终端应用程序，改为 Windows Terminal。
- 外观->在选项卡中显示亚力克效果，选择启用。
- 配色方案，这里可以根据自己喜好调整。
- 配置文件默认值->外观->字体，改为`MesloLGS NF`字体，字号按照自己屏幕大小选择，再开启亚力克效果，透明度选择 70%左右。

这样一来，Windows Terminal 的配置就算完成了。当然如果你对自带的配色方案不满意，也可以从网络上寻找一些好看的配色方案， 其他设置也可以根据自己喜好进行修改，这里就不多做介绍了。

## oh-my-posh

### 安装 oh-my-posh

oh-my-posh 是一个 Powershell 的主题项目，可以将 Powershell 美化成类似 ohmyzsh 的效果。安装 oh-my-posh 也很简单，运行下面的命令即可。`posh-git`是一个在提示符中显示 git 仓库信息的包，建议同时安装。

```Powershell
Install-Module posh-git -Scope CurrentUser
Install-Module oh-my-posh -Scope CurrentUser
```

安装成功之后就可以在终端中显示主题了。

```Powershell
# 首先需要加载oh-my-posh模块
Import-Module oh-my-posh
# 然后指定一个主题
Set-PoshPrompt -Theme gmay
```

显示效果如下。
![Powershell显示效果](/img/ohmyposh主题.png)

当然这里还有很多其他主题可供选择，<https://ohmyposh.dev/docs/themes>。如果你不喜欢这些主题，甚至还可以自己编写 ohmyposh 主题。

### 对所有终端生效

在终端中配置的 oh-my-posh 只能在当前终端生效，为了让它能够在所有 Powershell 中永久生效，需要在配置文件中编辑。

在 Powershell 中运行以下命令，用 vscode 打开 Powershell 的配置文件，如果你没有 vscode，也可以改成 notepad 用记事本来编辑配置文件。

```powershell
code $PROFILE
```

在配置文件中添加的所有命令，都将在每次打开 Powershell 时运行，这样一来配置就可以对所有 Powershell 窗口生效了。

```powershell
Import-Module oh-my-posh
Set-PoshPrompt -Theme gmay
```

配置完毕后，打开一个新的终端，应当可以看到新终端也同时应用了我们刚才设置的主题，这样 oh-my-posh 就配置成功了。

## Terminal-Icons

Terminal-Icons 是一个为 Powershell 显示文件类型图标的 Powershell 模块，显示的图标同样基于 nerd-fonts。不过刚才我们已经安装并在终端中使用了 nerd-fonts，所以放心安装就可以了。

```powershell
Install-Module -Name Terminal-Icons -Scope CurrentUser
```

安装完毕后，在终端中导入模块，再运行一下`Show-TerminalIconsTheme`命令，就可以看到 Terminal-Icons 为文件类型显示图标的例子了。

```powershell
Import-Module -Name Terminal-Icons
Show-TerminalIconsTheme
```

同样的，为了让所有终端都能生效，应该将下面一行添加到`$PROFILE`中。这样，以后再使用`dir`等命令显示文件的时候，都会显示出对应的图标。

```powershell
Import-Module -Name Terminal-Icons
```

## z.lua

### 安装 z.lua

z 是一个 linux 下知名的终端目录跳转插件，可以智能的帮助我们在多个目录中跳转。不过这个插件是用 shell 语言写成的，所以速度并不理想。因此就有了 z.lua 这个项目，是用 lua 脚本语言重新实现 z 的功能，速度更快，兼容性也更好。

因为是用 lua 语言写成的，所以首先需要安装 lua 语言，这很简单，直接用 scoop 安装即可。

```sh
scoop install lua
```

然后需要下载 z.lua 项目，这里推荐直接用 git 将项目克隆到用户主目录下。

```sh
git clone https://github.com/skywind3000/z.lua.git ~/z.lua
```

然后在`$PROFILE`中添加下面一行，这样以后在使用终端的时候都可以用`z`命令来实现跳转了。

```powershell
Invoke-Expression (& { (lua $HOME/z.lua/z.lua --init powershell once enhanced) -join "`n" })
```

### 使用 z.lua

那么这个东西到底要怎么用呢？其实很简单。

```powershell
# 首先需要在终端中切换几次不同的目录，ab是两个路径不同的目录
cd a
cd b
# 然后z.lua就会记住切换的选择，下次直接输入目录名甚至一部分即可实现跳转
z a
z b
```

这个项目是咱们国内大佬写的，所以还有官方的中文文档，对 z.lua 的使用方法有更加详细和深入的讲解，务必要阅读一遍，之后你就可以用它来实现畅快的目录跳转了，<https://github.com/skywind3000/z.lua/blob/master/README.cn.md>。

## PSReadLine

想让 Powershell 也拥有提示和补全功能？PSReadLine 可以帮你，这是一个可以增强终端体验的工具。

### 安装 PSReadLine

确保你使用的是 Powershell 7.2，然后运行下面的命令。

```powershell
Install-Module PSReadLine -AllowPrerelease -Force
# 或者你喜欢稳定版
Install-Module PSReadLine -Scope CurrentUser
```

### 使用 PSReadLine

要使用 PSReadLine，同样需要在`$PROFILE`中添加一些配置。如果想了解下面配置的意思，可以参考官方文档，<https://docs.microsoft.com/en-us/powershell/module/psreadline/about/about_psreadline>

```powershell
Import-Module PSReadLine
Set-PSReadLineOption -EditMode Emacs
Set-PSReadLineOption -PredictionSource HistoryAndPlugin
Set-PSReadLineOption -PredictionViewStyle ListView
Set-PSReadLineOption -BellStyle None
Set-PSReadLineKeyHandler -Chord 'Ctrl+d' -Function DeleteChar
```

其实本来还想写 PSFzf 的，但是在我这里配置了 PSFzf 之后，终端打开速度有点慢，居然要两秒多，虽然不是不能用但是感觉还是有点慢，所以最后还是放弃了。目前配置完以后需要 1200 毫秒左右，感觉还行。
