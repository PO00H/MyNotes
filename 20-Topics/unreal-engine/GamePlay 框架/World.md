---
title: World
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# World

## 一句话定义

> [!abstract]
> World（世界）= ==装下一切的最上层容器==。所有 [[Actor]] 和组件都"活"在某个 World 里，并在其中渲染。它代表当前这张地图的运行环境。

## 📖 要点

- **装了什么**：持久关卡（Level）+ 当前地图里所有对象——[[GameMode]]、[[GameState]]、各种 Pawn 和 [[Controller]] 列表。
- **和 Level 的关系**：World 是运行时容器，Level（关卡 / 地图）是它包含的内容；一个 World 可由多个 Level 组成（如关卡流送）。
- **代码里常见**：几乎所有"在世界里发生"的操作都从 `GetWorld()` 拿到当前 World 起手（生成 Actor、射线检测、定时器）。
- **PIE 也有 World**：编辑器里点 Play，会单独开一个游戏用的 World，和编辑器的 World 分开。

> [!warning] 易错点
> - **混淆 World 和 Level** → World = 运行容器，Level = 里面的内容（地图文件）。
> - **没有 World 上下文乱 Spawn** → 生成 Actor 等操作都依赖一个有效的 World。

## 连接

- [[Actor]] - 所有 Actor 都存在于某个 World 中
- [[GameMode]] - 每个 World 运行时由它定规则
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [虚幻引擎中的 Gameplay 框架 | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/gameplay-framework-in-unreal-engine?lang=zh-CN)

## 待深化

- [ ] 关卡流送（Level Streaming）与持久关卡
- [ ] World、Level、Sublevel 的层级关系
