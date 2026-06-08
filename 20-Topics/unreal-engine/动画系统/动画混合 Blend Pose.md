---
title: 动画混合 Blend Pose
tags: [UE, 动画系统]
created: 2026-06-08
status: 草稿
---

# 动画混合 Blend Pose

## 一句话定义

> [!abstract]
> Blend Pose = ==按一个条件在多个动画之间切换/混合==。`by bool` 二选一，`by int` 多选一，每个动画还能设过渡时间。

## 📖 要点

| 节点 | 用途 |
|---|---|
| **Blend Poses by bool** | 二选一：true 走 True Pose、false 走 False Pose |
| **Blend Poses by int** | 多选一：按 0/1/2… 选；右键 `Add Blend Pin` 加分支 |
| **Blend Time** | 从其它动画过渡到这个 Pose 的时间（如 0.1 秒），让切换平滑 |

![[Pasted image 20260608215618.png]]

- 典型：`isMoving ? Walk : Idle`（by bool），把 [[动画蓝图]] EventGraph 算出的 `isMoving` 接进来。
- 选项本质和 `Switch`/枚举一致（见 [[枚举 Enum]]）。

> [!tip] 何时改用状态机
> ==动画两三个用 Blend Pose 就够；走/跑/跳/蹲一多，嵌套 Blend 就乱了 → 换 [[动画状态机 State Machine]]。==

## 连接

- [[动画系统]] - 所属（枢纽）
- [[动画蓝图]] - 在 AnimGraph 里用
- [[动画状态机 State Machine]] - 多状态时的替代
- [[布尔 Boolean]] / [[枚举 Enum]] - by bool / by int 的条件

## 来源

- 2026-06-08 - note6.8（创建动画蓝图）

## 待深化

- [ ] Blend Space（按速度/方向二维混合）
