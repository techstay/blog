---
title: "Visual Studio 2022 C++20标准新特性模块尝鲜"
date: 2022-01-03T06:29:43+08:00
tags:
  - windows
  - c++
categories:
  - c++
---

长久以来，C++一直有一个问题那就是编译复杂。所以现在最新的 C++20 标准就新增了模块特性，试图改善这个状况。不过因为各大编译器以及工具链对新标准的支持还不够完善，所以目前我们只能简单尝鲜一下。想要正式在项目中应用这个特性，还需要很长的时间。

这里我用 Visual Studio 2022 来向大家介绍一下。首先在 Visual Studio Installer 中安装 C++桌面开发的工作负载，同时在单个组件里找到对应的 C++模块库文件（如下图所示）。

![C++模块库文件](https://upload-images.jianshu.io/upload_images/832668-66f62d9d25c8cd8b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后随便新建一个 C++控制台程序，随便编译一下，这个时候我们还是使用默认的头文件形式来导入标准库。

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello world!\n";
}
```

然后打开项目属性对话框，找到配置属性->C/C++->语言，将 C++语言标准改为最新的，同时将启用实验性的 C++标准库模块改为是。

![项目属性配置](https://upload-images.jianshu.io/upload_images/832668-29e49164fd31f2f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这样一来我们就可以在项目中使用模块了。最简单的办法就是先试试标准库模块，将包含头文件的声明改为导入语句再编译试试。

```cpp
import std.core;

int main()
{
    std::cout << "Hello world!\n";
}
```

当然，我们也可以编写自己的模块。编写模块的时候，不能用常规的`cpp`作为文件扩展名，而要使用`ixx`作为扩展名，而且这时候我们的源代码也有了一个新名字，叫做模块接口文件。这里我新建一个`hello.ixx`文件作为模块接口文件。

```cpp
export module hello;

import std.core;

export void hello(std::string name)
{
    std::cout << "Hello, " + name << std::endl;
}
```

然后，我们就可以在程序中导入自己的模块了。

```cpp
import hello;
import std.core;

using namespace std;

int main()
{
    hello("techstay");
    cout << "你好，世界!" << endl;
}
```

可惜的是目前的工具链支持还不够完善，甚至连 ReSharper 都还没有支持模块特性，在运行上面的例子时候代码分析还提示了一些错误。希望一两年之内能够用上这个新特性吧。
