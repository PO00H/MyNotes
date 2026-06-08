---
title: Input Action (IA)
tags: [UE, 输入系统]
created: 2026-06-03
status: 草稿
---

# Input Action (IA)

## 一句话定义

> [!abstract]
> Input Action（IA）= ==一个抽象的"动作"==（跳跃、移动、开火），它==不关心具体按键==，只定义"这个动作长什么样"（值类型）以及触发/修饰规则。绑哪个键是 [[Input Mapping Context]] 的事。

## 📖 要点

- **建法**：内容浏览器右键 → `Input → Input Action`（命名习惯 `IA_Jump`）。
- **值类型 Value Type**（决定动作输出什么）：
	- Digital(bool)：开关型（跳跃、开火）。
	- Axis1D(float)：一维（油门、缩放）。
	- Axis2D(Vector2D)：二维（移动、视角）。
- 一个 IA 内部可配 **Triggers**（何时算触发）和 **Modifiers**（输出值怎么改）——见下。

## ⚙️ Triggers 触发器（何时算"触发"）

> ==生效范围==：写在 IA 里 → 对所有用它的按键生效；写在 [[Input Mapping Context]] 的某个键下 → 只对该键生效。

![[Pasted image 20260603103149.png]]

| Trigger | 含义 |
|---|---|
| **Pressed** | 按下瞬间 |
| **Released** | 抬起瞬间 |
| **Down** | 按住期间持续 |
| **Hold** | 按住达到时长才触发 |
| **Hold And Release** | 按住够久、抬起时触发 |
| **Tap** | 快速点按（短于阈值） |
| **Pulse** | 按住期间按节奏重复触发 |
| **Repeated Tap** | 连续点按 N 次 |
| **Chorded Action** | 需另一个 IA 同时按下（组合键） |
| **Combo** | 按特定序列（连招，Beta） |

## ⚙️ Modifiers 修饰器（改输出值）

> 生效范围同 Triggers。修改的是 IA 输出的 **Action Value**。

![[Pasted image 20260603103227.png]]

| Modifier | 作用 |
|---|---|
| **Negate** | 取反（如 S 键 = 前进的负方向） |
| **Scalar** | 按系数缩放 |
| **Dead Zone** | 摇杆死区，过滤微小抖动 |
| **Swizzle Input Axis Values** | 调换轴顺序（把 X 输入塞到 Y） |
| **Smooth / Smooth Delta** | 平滑输入 |
| **Scale By Delta Time** | 乘以帧时间（与帧率无关） |
| **Response Curve** | 输入响应曲线（指数/自定义） |
| **FOV Scaling / To World Space** | 视野缩放 / 转世界空间 |

> 💡 经典用法：W/S 共用一个"前后移动"IA，S 键加 **Negate** 就成了反方向——不必建两个动作。

## ⚡ Action 事件（蓝图里怎么响应）

蓝图右键 `EnhancedInputAction IA_xxx` 节点，五个执行引脚按时机触发：

![[Pasted image 20260603103236.png]]

| 事件 | 触发时机 |
|---|---|
| **Started** | ==按下的一瞬间== |
| **Triggered** | ==按住时每帧==（满足触发条件期间） |
| **Ongoing** | 特殊触发条件（如 Hold）==检测中、尚未成功==时每帧 |
| **Canceled** | 特殊触发条件==没满足、失败==时（如 Hold 没按够就松手） |
| **Completed** | ==抬起的一瞬间== |

- 正常一次"按下→松开"：触发成功会先 `Triggered`（可能多帧）→ 松手 `Completed`。
- 数据输出引脚：`Action Value`（动作值）、`Elapsed Seconds`、`Triggered Seconds`、`Input Action`。

> [!warning] 易错点
> - **分不清 Triggered 和 Started**：Started 只在按下那一帧；Triggered 在满足条件期间每帧都来。
> - **Hold 没等够就松手** → 走 `Canceled` 而不是 `Completed`。
> - **移动想用 Triggered**：持续移动读 Triggered（每帧），别用 Started（只一次）。

## 连接

- [[输入系统]] - 所属系统（枢纽）
- [[Input Mapping Context]] - 把按键绑到本 IA
- [[变量类型]] - 值类型用到 bool / float / Vector2D

## 来源

- 2026-06-03 - 课程笔记（增强输入系统）

## 待深化

- [ ] Chorded Action（组合键）实操
- [ ] Modifier 顺序对最终值的影响
