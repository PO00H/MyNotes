---
title: Delay 延迟
tags: [UE, 蓝图基础]
created: 2026-06-07
status: 草稿
---

# Delay 延迟

## 一句话定义

> [!abstract]
> Delay = ==等待 Duration 秒，再继续往下执行==。`Retriggerable Delay` = 可重复触发的延迟——计时途中再被触发会**重新计时**。

## 📖 要点

![[Pasted image 20260607164607.png]]

| 节点 | 行为 |
|---|---|
| **Delay** | 等 `Duration` 秒 → 走 `Completed`。计时途中再触发会**忽略**（已有一个在跑） |
| **Retriggerable Delay** | 计时途中再触发会==重置倒计时==（重新从头等） |

> [!tip] Retriggerable 的经典例子
> 刺客信条里"敌人发现你"的 UI：每次再次被发现就**重置计时**，只有**持续一段时间没再被发现**，UI 才消失。=="最后一次触发后再等 N 秒"==——这正是 Retriggerable Delay。

> [!warning] 只能放进事件，不能放函数
> Delay 会跨帧等待，==不能放在普通函数里==（函数必须当帧返回），只能放事件图表 / [[自定义事件 CustomEvent]] 里。

> [!warning] 也别在 for 循环 / Sequence 里用 Delay
> ==蓝图 For 循环底层是 [[Sequence]] 实现的==，所以在 for / Sequence 里放 Delay **无效**（不会逐次等待）。要"等一步再下一步"就老实把节点连成一串。

## 连接

- [[蓝图基础]] - 所属（枢纽）
- [[自定义事件 CustomEvent]] - Delay 只能放事件里
- [[Timeline 时间轴]] - 同样是跨帧的时间控制

## 来源

- 2026-06-07 - 课程笔记（第三节·延迟/异步）

## 待深化

- [ ] Delay vs Timer（Set Timer by Event）的区别
- [ ] 异步节点（Latent Function）的概念
