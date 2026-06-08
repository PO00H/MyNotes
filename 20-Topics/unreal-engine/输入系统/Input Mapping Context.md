---
title: Input Mapping Context (IMC)
tags: [UE, 输入系统]
created: 2026-06-03
status: 草稿
---

# Input Mapping Context (IMC)

## 一句话定义

> [!abstract]
> Input Mapping Context（IMC）= ==一张"按键 → 动作"的映射表==。它把具体按键连到 [[Input Action]]，而且==可以整张挂载 / 卸载==——这就是增强输入能"运行时切换输入方案"的关键。

## 📖 要点

- **建法**：内容浏览器右键 → `Input → Input Mapping Context`（命名 `IMC_Default`）。
- **里面填什么**：一行行的「IA ← 按键」绑定，例：`IA_Jump ← Space`、`IA_Move ← W/A/S/D`。
- **每个按键可加自己的 Triggers / Modifiers**：==只对这个键生效==（对比：写在 [[Input Action]] 里则对所有键生效）。
- **必须挂载才生效**：在 PlayerController / Pawn 里调 `Add Mapping Context`（通过 `EnhancedInputLocalPlayerSubsystem`）把 IMC 加给玩家。
- **优先级 Priority**：可同时挂多张 IMC，数字大的优先；用来做"基础操作 + 临时覆盖"。

## 📖 教学（核心原理）

### 为什么要"上下文"

- ==不同场景需要不同键位==：走路一套、开车一套、菜单一套。
- 做法：每种状态一张 IMC，进入时 `Add`、离开时 `Remove`，无需改动 [[Input Action]] 本身。
- 一句话：**IMC 是可热插拔的"键位方案"。**

### 挂载流程

1. 玩家被 PlayerController 接管。
2. 拿到 `EnhancedInputLocalPlayerSubsystem`。
3. `Add Mapping Context(IMC, Priority)`。
4. 此后该 IMC 里的按键才会触发对应 IA。

> [!warning] 易错点
> - **输入完全没反应** → 八成==忘了 Add Mapping Context==（建了 IA/IMC 不挂载等于没接线）。
> - **两张 IMC 冲突** → 用 Priority 区分；高优先级覆盖低的。
> - **键位改了到处生效** → 那是改到 IA 里了；只想改一个键就在 IMC 的该键下配。

## 连接

- [[输入系统]] - 所属系统（枢纽）
- [[Input Action]] - IMC 绑定的目标动作
- [[Controller]] - 通常在 PlayerController / Pawn 里挂载 IMC
- [[Pawn]] - 输入最终驱动被操控的 Pawn

## 来源

- 2026-06-03 - 课程笔记（增强输入系统）

## 待深化

- [ ] `Add Mapping Context` 的蓝图 / C++ 具体节点
- [ ] 多 IMC + Priority 的实际分层设计
