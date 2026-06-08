---
title: 动画状态机 State Machine
tags: [UE, 动画系统]
created: 2026-06-08
status: 草稿
---

# 动画状态机 State Machine

## 一句话定义

> [!abstract]
> 状态机 = 用==「状态 + 转换条件」管理复杂动画切换==（Idle/Walk/Jump…）。比 [[动画混合 Blend Pose]] 更适合多状态——同一时刻只处于一个状态。

## 📖 要点

- **建法**：AnimGraph 右键 → `State Machine` → 双击进去。
- **组成**：
	- **状态（State）**：拖一个动画进去即一个状态（如 Idle、Walk）。
	- **转换条件（Transition）**：状态间连线，双击线写条件（如 `isMoving` → 从 Idle 切 Walk）。
	- **默认状态**：入口（Entry）必须连一个默认状态（绿线），否则报警告。
- **动画不循环？** 选中状态/动画 → 细节面板勾 `Loop Animation`。
- ==同一时刻只一个状态==：处于某状态时，只判断从它出发的转换条件。

![[Pasted image 20260608224853.png]]

> [!info] 官方 Locomotion 怎么搭（参考）
> 嵌套混合：Locomotion（走/跑混合）+ 跳跃（**起跳 → 下落 loop → 落地** 三段）再混到一起。复杂角色都是状态机套状态机。

> [!warning] 易错 / 待验证
> - 没默认状态 → 警告、跑不起来。
> - `Conduit`（导管）/ `State Alias`（别名）官方这例没怎么用，先不深究。
> - ⚠️ **待验证**：`Can Character Step Up On`（能否踏上去/踩尸体）老师没调清楚。

## 连接

- [[动画系统]] - 所属（枢纽）
- [[动画混合 Blend Pose]] - 简单切换的替代（少状态用它）
- [[动画蓝图]] - 状态机放在 AnimGraph 里
- [[枚举 Enum]] - 状态思想和枚举状态机相通

## 来源

- 2026-06-08 - note6.8（动画状态机）

## 待深化

- [ ] Conduit / State Alias 的用途
- [ ] Motion Matching（更先进的运动方案）
