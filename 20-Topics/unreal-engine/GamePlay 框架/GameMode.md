---
title: GameMode
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# GameMode

## 一句话定义

> [!abstract]
> GameMode = ==一局游戏的"宪法 + 总指挥"==。它定义玩法规则，并决定这局用哪些类（用哪个 PlayerController、哪个默认 Pawn、哪个 HUD）。加载地图时==第一个被生成==，再由它生成其余。

## 📖 要点

- **职责**：
	- 定规则（如夺旗、计分、胜负条件）。
	- ==指定要用的其他类==：DefaultPawn、PlayerController、HUD、GameState…
	- 控制玩家出生、重生等流程。
- **生成时机**：==加载地图（Level）时自动生成==，整局的起点。
- **唯一性**：服务器/单机上一局只有一个 GameMode 实例在管全场。
- **与邻居的分工**：
	- GameMode：规则 + 决定用哪些类。
	- [[GameState]]：记全局信息（比分）。
	- [[PlayerState]]：记单个玩家信息（血量/物品）。

## ⚡ 怎么设置

**项目默认 GameMode**

![[Pasted image 20260602230940.png]]

- `项目设置 → Maps & Modes → Default GameMode`。

**为单个 Level 覆盖**

![[Pasted image 20260602231008.png]]
![[Pasted image 20260602231019.png]]

- 打开关卡 → `World Settings → GameMode Override` → 这张地图用专属规则，覆盖项目默认。

> [!warning] 易错点
> - **改了规则全项目生效** → 只想改一张图就用 `World Settings` Override，别动项目默认。
> - **把玩家数据放 GameMode** → 全局数据放 GameState，玩家个人数据放 PlayerState。
> - **GameMode 在客户端找不到** → 多人游戏里 GameMode 只存在于服务器（客户端只有 GameState）。

## 连接

- [[GamePlay 框架]] - 总览（运行时层级的顶点）
- [[Controller]] / [[Pawn]] - GameMode 指定要生成的类
- [[GameState]] / [[PlayerState]] - 配套的数据类

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Game Mode and Game State | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/game-mode-and-game-state-in-unreal-engine)

## 待深化

- [ ] GameMode vs GameModeBase 的区别
- [ ] 出生点（PlayerStart）与重生流程
