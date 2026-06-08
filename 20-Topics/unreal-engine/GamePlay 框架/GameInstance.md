---
title: GameInstance
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# GameInstance

## 一句话定义

> [!abstract]
> GameInstance = ==整局游戏的"常驻大脑"==。从启动到退出==始终是同一个实例==，切地图、进菜单都不销毁——专门存"必须跨关卡活着"的数据和系统。

## 📖 要点

- **核心特性**：==生命周期 = 整个游戏进程==。地图切换、菜单往返都维护同一个 GameInstance。
- **存什么**：跨关卡要保留的东西——玩家存档、当前难度、登录态、在线服务连接。
- **和 GameMode 的对比**（关键区分）：

| | 生命周期 | 适合存 |
|---|---|---|
| **GameInstance** | ==整局不变== | 跨关卡数据（存档、设置） |
| **[[GameMode]]** | ==每张地图重建== | 这一关的规则 |

- **子系统（Subsystem）**：可挂 GameInstance Subsystem，把"全程常驻的功能模块"（如在线服务）独立管理，比全塞一个类干净。

> [!warning] 易错点
> - **把跨关卡数据放 GameMode** → 切地图就没了；要常驻就放 GameInstance。
> - **什么都往 GameInstance 塞** → 只放"真的需要全程存在"的；临时数据用 GameState / PlayerState。

## 连接

- [[GameMode]] - 对比：每关重建 vs 全程常驻
- [[World]] - 切换的是 World，GameInstance 不随之销毁
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [虚幻引擎中的 Gameplay 框架 | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/gameplay-framework-in-unreal-engine?lang=zh-CN)

## 待深化

- [ ] GameInstance Subsystem 的创建与用途
- [ ] 跨关卡传数据的几种方式对比
