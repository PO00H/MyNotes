---
title: 循环 For Each 与 For Loop
tags: [UE, 蓝图基础, 控制流]
created: 2026-06-04
status: 草稿
---

# 循环 For Each 与 For Loop

## 一句话定义

> [!abstract]
> 循环 = ==把同一段逻辑重复执行多次==。遍历一个数组用 **For Each Loop**，按固定次数跑用 **For Loop**。想中途退出，得用带 **Break** 的版本。

## 📖 要点

![[Pasted image 20260604110506.png]]

### For Each Loop（遍历数组，最常用）

| 引脚 | 含义 |
|---|---|
| **Array** | 要遍历的数组（如 Trace 的 Out Hits） |
| **Loop Body** | 循环体，==每个元素跑一次== |
| **Array Element** | 当前这个元素 |
| **Array Index** | 当前下标（==从 0 开始==） |
| **Completed** | 全部跑完后执行一次 |

- ==循环几次？== = **数组的长度**（有几个元素就几次），不用手动设。

### For Loop（按次数）

- 设 `First Index` / `Last Index`，从头跑到尾，输出 `Index`。
- 适合"不依赖数组、就想跑 N 次"。

### 怎么中途退出（Break）

> [!warning] 普通 For Each Loop 没有 Break 引脚，会一口气跑完
> 想提前退出 → 换成 **`For Each Loop with Break`**（或 `For Loop with Break`），它多一个 **Break** 执行输入。在循环体里满足条件就触发 Break，立即停止。

典型连法：

```
For Each Loop with Break
  └─ Loop Body ─▶ Branch（如"是敌人吗？"）
                   ├─ True ─▶ (做事) ─▶ Break   ← 提前结束
                   └─ False ─▶ 继续下一个
```

> [!tip] 用 C++ 底子秒懂
> - `For Each Loop` = `for (auto& e : array)`
> - `For Loop` = `for (int i=first; i<=last; i++)`
> - `Break` 引脚 = `break;`
> - `Array Index` = 下标 `i`
> 口诀：**遍历全部→For Each；要找到就停→with Break；纯跑 N 次→For Loop。**

> [!warning] 易错点
> - **想中途退却用了普通版** → 退不掉，换 with Break。
> - **下标越界** → 别手动 `Array[i]` 乱取，遍历优先用 For Each。
> - **在循环里改正在遍历的数组** → 容易出错，先收集再处理。

## 连接

- [[容器类型]] - For Each 遍历的就是数组
- [[主动碰撞检测 Trace]] - Multi 检测的 Out Hits 用 For Each 遍历
- [[布尔 Boolean]] - 配 Branch 判断是否 Break

## 来源

- 2026-06-04 - 课程笔记（循环）

## 待深化

- [ ] While Loop（条件循环）
- [ ] 循环里配合 Delay 的注意事项
