---
title: PlayerState
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# PlayerState

## 一句话定义

> [!abstract]
> PlayerState = ==单个玩家的"信息卡"==。记录跟某一个玩家绑定的数据：血量、子弹、得分、物品。==每个玩家一份==，跟着玩家走。

## 📖 要点

- **存什么**：==单个玩家==的持久信息——名字、得分、生命值、物品栏。
- **谁有它**：每个连入的玩家各自一份。
- **关键特性**：==Pawn 死了重生，PlayerState 还在==——所以"该跨越死亡保留"的数据（如总得分）放这里，而不是放 [[Pawn]]。
- **和 GameState 的分工**：[[GameState]] 记==全局==（比分总表），PlayerState 记==这一个玩家==（我的分）。
- **继承链位置**：是一种 [[Actor]]（基类 `APlayerState`）。

> [!warning] 易错点
> - **把血量放 Pawn** → Pawn 一死就没了；要保留就放 PlayerState。
> - **把数据放 [[Controller]]** → Controller 管操控逻辑，数据归 PlayerState。

## 连接

- [[GameState]] - 对应的"全局版"
- [[Controller]] - 玩家的操控手，与 PlayerState 配对
- [[Pawn]] - 临时身体（会死会换），持久数据不放这
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Player State | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/game-mode-and-game-state-in-unreal-engine)

## 待深化

- [ ] PlayerState 在重生 / 切换 Pawn 时如何保留
- [ ] 多人下的属性复制
