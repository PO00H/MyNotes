---
title: 主动碰撞检测 Trace
tags: [UE, 碰撞]
created: 2026-06-04
status: 草稿
---

# 主动碰撞检测 Trace

## 一句话定义

> [!abstract]
> 主动检测 = ==我主动发射一条"看不见的射线/形状"，去问"路径上碰到了什么"==。需要你在某个时机（开火、交互、检测脚下）**手动调用**——不是等事件，而是主动查询。

## 📖 要点

![[Pasted image 20260604101810.png]]

### 三个维度组合出一堆 Trace 节点

| 维度 | 选项 | 含义 |
|---|---|---|
| **形状** | Line / Box / Sphere / Capsule | 用线还是带体积的形状去扫 |
| **依据** | By Channel / For Objects / By Profile | 按"可见性等通道" / 按"对象类型" / 按"碰撞预设"筛 |
| **数量** | Single / Multi | 只要第一个命中 / 要全部命中 |

![[Pasted image 20260604101828.png]]

> 形状 × 数量就组合出常见的那一排节点（Line/Box/Sphere/Capsule 各有 Single/Multi）。

### Single vs Multi（最重要的区别）

- **Single**：返回**第一个**命中 → 输出 `Out Hit`（单个 Hit Result）。
- **Multi**：返回**所有**命中 → 输出 `Out Hits`（数组）→ 用 [[循环 For Each 与 For Loop\|For Each Loop]] 遍历。

![[Pasted image 20260604102143.png]]

### 读取命中结果

- 命中信息是个 **Hit Result** 结构体 → 用 `Break Hit Result` 拆出：`Hit Actor`（撞到谁）、`Location`（撞点）、`Normal`（表面朝向）等。

### Draw Debug Type（调试可视化）

![[Pasted image 20260604111417.png]]

| 选项 | 效果 |
|---|---|
| **None** | 不画（正式发布用） |
| **For One Frame** | 只画一帧（每帧检测时用） |
| **For Duration** | 画一段时间 |
| **Persistent** | 一直留着 |

> ==看不见的射线，靠 Draw Debug 画出来==——调检测必开，否则你不知道线射到哪了。

> [!warning] 易错点
> - **检测不到东西** → 目标的 `Collision Enabled` 关了，或通道响应是 Ignore；Trace 至少要目标在该通道上是 Block/Overlap。
> - **Multi 只处理了一个** → `Out Hits` 是数组，要用 For Each 遍历（见 [[循环 For Each 与 For Loop]]）。
> - **射线起点终点搞反/太短** → Start/End 是世界坐标，常用 `角色位置` 到 `角色位置 + 朝向 × 距离`。

## 连接

- [[碰撞 Collision]] - 所属系统（枢纽）
- [[被动碰撞检测 事件]] - 对照：被动是"等通知"
- [[循环 For Each 与 For Loop]] - 遍历 Multi 的 Out Hits
- [[结构体类型]] - Hit Result 是结构体，用 Break 拆

## 来源

- 2026-06-04 - 课程笔记（碰撞·主动检测）

## 待深化

- [ ] By Channel / For Objects / By Profile 三者的具体取舍
- [ ] 截图补：一次完整的 LineTrace 开火检测连法
