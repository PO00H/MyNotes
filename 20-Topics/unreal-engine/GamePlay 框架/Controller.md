---
title: Controller
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# Controller

## 一句话定义

> [!abstract]
> Controller = ==操控 Pawn 的"那只看不见的手"==。它是非实体 Actor（在世界里没有身体），通过"附身"（Possess）一个 [[Pawn]] 来指挥它的行动。

## 📖 要点

- **非实体**：Controller 自己==没有模型、没有位置感==，它只负责"下命令"。身体是 Pawn。
- **两种**：
	- **PlayerController**：人类玩家用——接收键鼠/手柄输入，转成对 Pawn 的指令。==同一时刻只有一个==。
	- **AIController**：AI 用——靠行为树/导航等人工智能驱动 Pawn。
- **手与身体分离的好处**：换 Pawn 不用换控制逻辑——同一个 PlayerController 可以 Possess 不同 Pawn（如切换载具/角色）。

> [!info] 类比
> 把 **Controller 想成"灵魂/玩家意志"**，**Pawn 想成"身体"**。灵魂可以换身体，身体没灵魂就瘫着不动。

> [!warning] 易错点
> - **Pawn 不响应输入** → 没被 Controller Possess，或输入绑在了错的地方。
> - **把数据塞进 Controller** → 玩家的血量/物品该放 [[PlayerState]]，不是 Controller。

## 连接

- [[Pawn]] - 被它操控的身体
- [[GamePlay 框架]] - 总览
- [[PlayerState]] - 玩家数据存这里

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Controller | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/controllers-in-unreal-engine)

## 待深化

- [ ] Possess / UnPossess 的蓝图节点
- [ ] PlayerController 的输入映射（Enhanced Input）
