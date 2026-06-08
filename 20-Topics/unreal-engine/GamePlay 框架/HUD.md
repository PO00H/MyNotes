---
title: HUD
tags: [UE, GamePlay框架, UI]
created: 2026-06-02
status: 草稿
---

# HUD

## 一句话定义

> [!abstract]
> HUD = ==画在屏幕最上层的 UI==（准星、血条、小地图）。它覆盖在游戏画面之上，==每个人类玩家一份==，绘制自己的视口。

## 📖 要点

- **干什么**：显示叠加在画面上的信息元素——血量、弹药、得分、提示。
- **谁有它**：每个由人类控制的玩家各自一个实例（对应各自视口）。
- **两条路**（现代 UE 常用后者）：
	- **HUD 类**：老式，用 C++/蓝图在屏幕上直接画（DrawText/DrawTexture）。
	- ==UMG==（[[UMG]] 待创建）：可视化拖拽做界面，主流做法，更灵活。
- **继承链位置**：是一种 [[Actor]]（基类 `AHUD`）。

> [!warning] 易错点
> - **复杂界面硬用 HUD 画** → 用 UMG（Widget Blueprint）效率高得多。
> - **HUD 数据从哪来** → 通常读 [[PlayerState]] / [[GameState]] 再显示。

## 连接

- [[Controller]] - HUD 归玩家的 PlayerController 管
- [[PlayerState]] / [[GameState]] - HUD 显示的数据来源
- [[UMG]] - 现代 UI 做法（待创建）
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [User Interfaces and HUDs | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/user-interfaces-and-huds-in-unreal-engine)

## 待深化

- [ ] HUD 类 vs UMG 的取舍
- [ ] 拆出 [[UMG]] 原子笔记（你简历里做过 UMG）
