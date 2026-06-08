---
title: GameState
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# GameState

## 一句话定义

> [!abstract]
> GameState = ==全场共享的"记分板"==。记录跟整局游戏相关、所有玩家都该看到的信息：比分、目标、当前所有玩家列表。由 [[GameMode]] 配套生成。

## 📖 要点

- **存什么**：==全局==、大家都要同步看到的数据——队伍比分、倒计时、关卡目标。
- **谁有它**：一局==只有一个==，服务器和所有客户端都持有同一份（自动同步）。
- **和 GameMode 的分工**：
	- GameMode 定==规则==（怎么玩）；GameState 记==状态==（现在玩到哪了）。
	- 多人游戏里：客户端==看不到 GameMode==（只在服务器），但==看得到 GameState==——所以要让客户端知道的信息放这里。
- **继承链位置**：是一种 [[Actor]]（基类 `AGameStateBase`）。

> [!warning] 易错点
> - **把单个玩家的数据塞进 GameState** → 那是 [[PlayerState]] 的活；GameState 只管全局。
> - **在客户端读 GameMode** → 读不到，改读 GameState。

## 连接

- [[GameMode]] - 配套生成它的总指挥
- [[PlayerState]] - 对应的"单玩家版"
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Game Mode and Game State | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/game-mode-and-game-state-in-unreal-engine#gamestate)

## 待深化

- [ ] GameStateBase vs GameState 区别
- [ ] 属性复制（Replication）如何同步到客户端
