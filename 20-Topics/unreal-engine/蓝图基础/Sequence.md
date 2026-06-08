---
title: Sequence
tags: [UE, 蓝图基础, 控制流]
created: 2026-06-08
status: 草稿
---

# Sequence

## 一句话定义

> [!abstract]
> Sequence = ==按 Then0 → Then1 → … 顺序点火==。普通节点会**等上一条链跑完再点下一个**；==只有遇到异步节点（Delay/Timeline）才不等待==。真正价值是**防长逻辑中途出错导致后续不执行**。

## 📖 要点

- **顺序点火**：普通节点 Then0 的整条链**跑完** → 才点 Then1 → …，按序、且都在**同一帧**内（Then0 确实等它跑完）。
- **遇异步才不等**：若 Then0 链里有 [[Delay 延迟]] / Timeline，Sequence **不等它完成**，立刻点 Then1 → 看起来"并行"。=="不等上一步"只在有异步节点时成立。==
- **真正用途**：UE 里==一条长逻辑中某节点出错，后面节点全不执行==（但不崩溃）。用 Sequence 切成几段，==某段出错不连累其它段==。
- **整理作用**：长线变几段，好读。

![[Pasted image 20260608223712.png]]

> [!warning] 致命坑：别在 for / Sequence 里用 Delay
> ==蓝图的 For 循环底层就是 Sequence 实现的== → 所以**在 For 循环或 Sequence 里用 [[Delay 延迟]] 无效**（不会逐次等待）。需要"等一步再下一步"时，==老老实实把节点连成一串==，别用 Sequence。

## 连接

- [[蓝图基础]] - 所属（枢纽）
- [[Delay 延迟]] - 别在 Sequence/for 里用它
- [[循环 For Each 与 For Loop]] - for 底层就是 Sequence

## 来源

- 2026-06-08 - note6.8（动画状态机·补充）

## 待深化

- [ ] Gate / DoOnce / MultiGate 等流程节点
