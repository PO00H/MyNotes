---
title: Timeline 时间轴
tags: [UE, 蓝图基础]
created: 2026-06-07
status: 草稿
---

# Timeline 时间轴

## 一句话定义

> [!abstract]
> Timeline = ==在一段时间内平滑改变一个数值==的节点。简单说就是"控制动作拆分播放"——开门、渐隐、平移、缩放这类**随时间变化的动画**，都靠它。

## 📖 要点

![[Pasted image 20260605101218.png]]

- **建法**：事件图表右键 → `Add Timeline` → 双击进去**画曲线**。
- **轨道类型**：Float（一个值）/ Vector / Color / Event（在某时间点触发）。
- **输入引脚**：`Play`（正向播）/ `Reverse`（倒放）/ `Stop` / `Play from Start`。
- **输出引脚**：
	- `Update`：==播放期间每帧输出当前值==（接到 SetRelativeRotation 等去驱动）。
	- `Finished`：播完触发一次。
	- `Value`：当前曲线值。

![[Pasted image 20260605101228.png]]

> [!tip] 开门的经典用法
> Timeline 曲线 0→1，`Value × -90` 喂给门的 `Set Relative Rotation (Yaw)`：`Play` 开门、`Reverse` 关门。==一条 Timeline 正反放，就搞定开关两个动作。==

> [!warning] 必须放进事件，不能放函数
> Timeline 会跨帧播放，所以==只能放在事件图表（自定义事件）里，不能放进普通函数==（同 [[Delay 延迟]]）。见 [[自定义事件 CustomEvent]]。

## 连接

- [[蓝图基础]] - 所属（枢纽）
- [[自定义事件 CustomEvent]] - Timeline 只能放事件里
- [[数值类型]] - Value 通常是 Float
- [[结构体类型]] - 驱动的常是 Rotation（Rotator）

## 来源

- 2026-06-05 - 课程笔记（第一节·时间轴）

## 待深化

- [ ] 曲线编辑（缓入缓出 ease）
- [ ] Event 轨道在特定时间点触发
