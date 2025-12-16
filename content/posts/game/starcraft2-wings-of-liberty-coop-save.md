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

## 前言

最近开始玩星际 2 的合作战役，可以最多三个人合作玩经典的单人战役模式，而且通关之后也可以像单人战役那样解锁科技。不过不知道为啥，科技解锁的非常慢，而且重复通关同一关也没办法重新获取技能点数。我玩了两天，科技也没点出多少，遂设想能不能自己修改一下存档，一次性获取所有技能点数，最后还真让我找到了。

## 修改数值

自由之翼合作战役的存档是`我的文档\StarCraft II\Accounts\xxx\xxx\Banks\xxx\BankCoop.SC2Bank`，`xxx`的部分是和账号相关的，每个人都不一样。这是一个 xml 文件，打开以后寻找`playerstats`一节，然后将三个科技点数的值改为 1000，这样当你通关以后就可以直接获得各 1000 的三种技能点，可以一次性把所有科技点满！以后就再也不用重复刷刷刷了！

<details>
<summary>XML</summary>

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

</details>

## 科技全解锁

上面的修改数值只能一次性解锁所有单位和科技，但是科技实验室里的异虫科技和星灵科技只能二选一，实在是很可惜。后来有一次我打的时候碰到了一个全解锁大佬，给我分享了全解锁的存档，这个存档可以同时解锁二选一的科技，非常强悍。开局就有双倍农民星轨，运营丝滑，各种黑科技加持下的雷诺简直比合作模式里还厉害。

国服开了之后，我研究了一下存档，重新整了一份存档，如需自取。

[完美存档链接](/file/BankCoop.SC2Bank)

## 存档文件

在[虫群之心合作战役存档](/posts/game/starcraft2-heart-of-swarm-coop-save)的文章里写过分析了，两个合作战役的存档大同小异，反正已经有了完美存档，就没必要太在意细节了。不过有一点值得注意一下，就是 22 关媒体轰炸的右下角有个建筑，打烂会解锁隐藏关卡，这一点在合作战役里也实现了。合作战役的隐藏关卡揭露黑幕，需要完成 22 关都条件并且保存游戏之后才能解锁。所以对应的存档部分也多了一条`wakawaka`。

<details>
<summary>XML</summary>

```xml
    <Section name="mission_22">
        <Key name="wakawaka">
            <Value flag="1"/>
        </Key>
        <Key name="zerg">
            <Value int="0"/>
        </Key>
        <Key name="played">
            <Value flag="1"/>
        </Key>
        <Key name="protoss">
            <Value int="0"/>
        </Key>
        <Key name="bonusCash">
            <Value int="0"/>
        </Key>
    </Section>
```

</details>
