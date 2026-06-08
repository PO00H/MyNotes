---
title: 布尔 Boolean
tags: [UE, 蓝图基础, 变量类型]
created: 2026-06-02
status: 草稿
---

# 布尔 Boolean

## 一句话定义

> [!abstract]
> Boolean（bool）= ==只有两个值的开关==：真（True）或假（False）。是所有"要不要 / 是不是"判断的基础——蓝图分支（Branch）的命根子。

## 📖 要点

- **取值**：仅 `True` / `False`，蓝图里是==红色==引脚。
- **核心搭档**：`Branch` 节点——bool 为真走一条线，为假走另一条（相当于 if）。
- **常见来源**：
	- 比较运算的结果（`>`、`==` 等输出 bool）。
	- 状态标记：`isAlive`、`hasKey`、`isOpen`。
- **命名习惯**：用 `is/has/can` 开头，读起来就是个问句（`isDead?`）。

> [!tip] 取反
> `NOT` 节点把 True↔False 翻转；多个 bool 用 `AND` / `OR` 组合判断。

## 连接

- [[变量类型]] - 所属家族（枢纽）
- [[数值类型]] - 比较运算常产出 bool

## 来源

- 2026-06-02 - 课程笔记

## 待深化

- [ ] Branch / FlipFlop / Gate 等流程控制节点
