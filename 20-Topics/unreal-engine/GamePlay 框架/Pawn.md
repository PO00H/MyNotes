---
title: Pawn
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# Pawn

## 一句话定义

> [!abstract]
> Pawn = ==能被"操控"的 Actor==。它是所有"可以被玩家或 AI 接管"的对象的基类——你在游戏里直接控制的那个身体，往往就是个 Pawn。

## 📖 要点

- **继承链位置**：`Object → Actor → **Pawn** → Character`。在 Actor 基础上加了==可被 [[Controller]] 操控==。
- **谁来控**：自己不会动，要靠一个 [[Controller]] "附身"（Possess）：
	- 玩家 → PlayerController
	- AI → AIController
- **可以有多个**：场景里能放一堆 Pawn，但==一个 PlayerController 同时只控一个==，要切换得重新 Possess。
- **裸 Pawn vs Character**：Pawn 本身不带移动逻辑；要开箱即用的走跑跳，用它的子类 [[Character]]。

> [!warning] 易错点
> - **放了 Pawn 却动不了** → 没有 Controller 来 Possess 它。
> - **想同时控制多个角色** → 不行，一个 Controller 一次一个，需切换。

## 连接

- [[Actor]] - 父类（Pawn 是一种 Actor）
- [[Character]] - 子类（带运动组件的 Pawn）
- [[Controller]] - 操控 Pawn 的那只手
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Pawn | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/pawn-in-unreal-engine)

## 待深化

- [ ] Possess / UnPossess 流程
- [ ] DefaultPawn、SpectatorPawn 的用途
