---
title: Character
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# Character

## 一句话定义

> [!abstract]
> Character = ==自带"会走路"的特殊 Pawn==。在 Pawn 基础上加了一套运动组件，开箱就能直立行走、奔跑、跳跃、飞行、游泳——做"人形可控角色"的首选起点。

## 📖 要点

- **继承链位置**：`Object → Actor → Pawn → **Character**`。在 Pawn 基础上加了==运动组件（CharacterMovementComponent）==。
- **白送的三件套**（典型）：
	- 胶囊碰撞体（Capsule）——角色的"身体范围"。
	- 骨架网格体（SkeletalMesh）——挂动画的模型。
	- CharacterMovement——处理走/跑/跳/重力/落地。
- **什么时候用**：做玩家角色、NPC 这类"人形会动"的对象 → 直接选 Character，省掉自己写移动。
- **什么时候不用**：载具、飞行器这种运动方式特殊的，可能直接从 [[Pawn]] 起步，自己写移动。

> [!warning] 易错点
> - **角色不动** → 同样要被 [[Controller]] Possess（它仍是 Pawn 的一种）。
> - **过度使用** → 不是所有可控物都该是 Character；非人形运动用裸 Pawn 更干净。

## 连接

- [[Pawn]] - 父类（Character 是一种 Pawn）
- [[Controller]] - 操控它的手
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Character | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/characters-in-unreal-engine)

## 待深化

- [ ] CharacterMovement 的常用参数（速度、跳跃高度、重力）
- [ ] 角色蓝图 + 动画蓝图的衔接
