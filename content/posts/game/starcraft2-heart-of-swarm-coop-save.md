---
title: "星际争霸2虫群之心合作战役全科技存档"
date: 2025-12-16T22:55:16+08:00
image: https://img.3dmgame.com/uploads/allimg/130330/180_130330133144_1.jpg
tags:
  - 星际争霸
  - 游戏
categories:
  - game
---

## 前言

星际国服开了以后，以前的自定义地图也逐渐回归了。最近虫群之心的合作战役也更新了，还得重新打，干脆研究一下直接改存档得了。正好以前我有修改自由之翼合作战役存档的经验，所以比较轻松的完成了。

值得一提的是虫群之心的战役做了一些优化，游戏开局就可以为每个兵种的科技四选一，无需通过关卡解锁，这一点还是很好的。不过也因为这一点，导致虫群之心没办法在像自由之翼那样做出全科技存档了。不过毕竟 ZIMBA，后续科技解锁了之后仍然很轻松，即便是没有解锁科技的新玩家也不会那么坐牢了。

## 存档文件内容

虫群之心的合作战役和自由之翼的一样，存档文件位于`我的文档\StarCraft II\Accounts\xxx\xxx\Banks\xxx\`目录下，存档文件名为`HotSCoopCampaign.SC2Bank`，存档文件是 XML 格式，很容易分析和修改，实在不行还可以交给 AI 来分析。

### 部队进化

虫群之心合作战役大幅度简化科技，英雄和部队的科技开局即可选择，等级只影响是否解锁。而部队的几种变体需要在对应的合作战役进化关卡中完成，完成进化关卡之后会有选择环节，选好之后即可写入战役存档。如果想要更换兵种变种，需要重新打一遍进化关卡，或者直接在存档里修改选择。合作战役比原版战役多了一种兵种进化，还是挺有意思的。不过后面的关卡我大部分还是用飞行宿主和大龙来打，战损低不吃经济。

<details>
<summary>XML</summary>

```xml
    <Section name="mutation">
        <Key name="mutalisk">
            <Value int="2"/>
        </Key>
        <Key name="ultralisk">
            <Value int="2"/>
        </Key>
        <Key name="roach">
            <Value int="2"/>
        </Key>
        <Key name="zergling">
            <Value int="4"/>
        </Key>
        <Key name="swarmhost">
            <Value int="3"/>
        </Key>
        <Key name="baneling">
            <Value int="1"/>
        </Key>
        <Key name="hydralisk">
            <Value int="3"/>
        </Key>
    </Section>
```

</details>

### 英雄

虫群之心大部分战役都有英雄 RPG，合作战役三位玩家都有自己的英雄，分别是`kerrigan`、`naktul`和`dowadiru`，英雄的技能分支保存在对应部分。

<details>
<summary>XML</summary>

```xml
    <Section name="kerrigan">
        <Key name="tier2">
            <Value int="1"/>
        </Key>
        <Key name="tier7">
            <Value int="2"/>
        </Key>
        <Key name="tier6">
            <Value int="3"/>
        </Key>
        <Key name="tier1">
            <Value int="1"/>
        </Key>
        <Key name="tier4">
            <Value int="1"/>
        </Key>
        <Key name="tier3">
            <Value int="3"/>
        </Key>
        <Key name="tier5">
            <Value int="3"/>
        </Key>
    </Section>
```

</details>

英雄的游玩数据保存在`playerstats`部分。

<details>
<summary>XML</summary>

```xml
    <Section name="playerstats">
        <Key name="kerrigan">
            <Value int="9999"/>
        </Key>
        <Key name="times_with_2">
            <Value int="1"/>
        </Key>
        <Key name="naktul">
            <Value int="9999"/>
        </Key>
        <Key name="times_with_1">
            <Value int="1"/>
        </Key>
        <Key name="times_with_3">
            <Value int="1"/>
        </Key>
        <Key name="dowadiru">
            <Value int="9999"/>
        </Key>
    </Section>
```

</details>

### 任务

虫群之心总共有 27 个任务，每个任务都有自己的数据，玩家等级会影响英雄技能的解锁，等级最高 70 级。

<details>
<summary>XML</summary>

```xml
    <Section name="mission_4">
        <Key name="times_played">
            <Value int="2"/>
        </Key>
        <Key name="mapcompleted">
            <Value flag="1"/>
        </Key>
        <Key name="levels_given">
            <Value int="0"/>
        </Key>
        <Key name="levels_bonus">
            <Value int="2"/>
        </Key>
        <Key name="herolevel">
            <Value int="70"/>
        </Key>
    </Section>
```

</details>

### 快捷键

这个也是我很喜欢的一个功能，在合作战役里可以保存你使用的建筑快捷键，开局即可直接使用，在也不用每次都需要重新编队了，而且对于新造的建筑也有效。当然这个功能最有用的还是自由之翼战役，人族建筑多编队麻烦，虫族就简单多了。

<details>
<summary>XML</summary>

```xml
    <Section name="controlgroups">
        <Key name="spire">
            <Value int="5"/>
        </Key>
        <Key name="hatchery">
            <Value int="4"/>
        </Key>
        <Key name="evolutionchamber">
            <Value int="5"/>
        </Key>
    </Section>
```

</details>

## 完美存档

最后修改完了之后，我也是成功的把英雄等级直接升级到了最高级，解锁了全部科技。不过呢其实意义也不大，自由之翼合作战役有全科技模式，可以在游戏前期就体验后期的科技和兵种，而且实验室的科技以被动形式存在，可以同时生效。但是虫群之心合作战役并没有全科技模式，打前期关卡照样得用白板兵来打，所以多打几关迟早也可以全解锁。

不过最后还是按照惯例放出存档链接，有需求自取。最后还有吐槽一句，我为了省事，直接用 Kilo Code 修改存档文件，结果直接用了 70K 的 token，一下子把我字节跳动上的免费 token 一下子用光了，还倒欠一块多，好在比较便宜。下次得老老实实设置一下限额，不能再超了。

[存档链接](/file/HotSCoopCampaign.SC2Bank)
