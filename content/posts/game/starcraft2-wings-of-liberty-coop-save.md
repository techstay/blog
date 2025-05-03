---
title: "星际争霸2自由之翼合作战役修改存档"
date: 2022-01-22T16:54:45+08:00
image: https://blz-contentstack-images.akamaized.net/v3/assets/blt0e00eb71333df64e/blt0c72fa572370924a/6621cf093e3ae61b4d769c56/game_features_legendary_multiplayer.webp
tags:
  - 星际争霸
  - 游戏
categories:
  - game
---

最近开始玩星际 2 的合作战役，可以最多三个人合作玩经典的单人战役模式，而且通关之后也可以像单人战役那样解锁科技。不过不知道为啥，科技解锁的非常慢，而且重复通关同一关也没办法重新获取技能点数。我玩了两天，科技也没点出多少，遂设想能不能自己修改一下存档，一次性获取所有技能点数，最后还真让我找到了。

自由之翼合作战役的存档是`我的文档\StarCraft II\Accounts\xxxxxxxx\xxxxxxx\Banks\xxxxxxx\BankCoop.SC2Bank`，`xxxxx`的部分是和账号相关的，每个人都不一样。这是一个 xml 文件，打开以后寻找`playerstats`一节，然后将三个科技点数的值改为 1000，这样当你通关以后就可以直接获得各 1000 的三种技能点，可以一次性把所有科技点满！以后就再也不用重复刷刷刷了！

```xml
<Section name="playerstats">
    <Key name="zerg">
        <Value int="1000"/>
    </Key>
    <Key name="protoss">
        <Value int="1000"/>
    </Key>
    <Key name="cash">
        <Value int="1000"/>
    </Key>
</Section>
```

[完美存档链接](/file/BankCoop.SC2Bank)
