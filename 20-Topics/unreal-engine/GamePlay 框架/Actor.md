---
title: Actor
tags: [UE, GamePlay框架]
created: 2026-06-02
status: 草稿
---

# Actor

## 一句话定义

> [!abstract]
> Actor = ==能放进关卡世界的一切==。摄像机、网格体、出生点、玩家……只要在世界里有"存在感"，它就是个 Actor。它是 GamePlay 框架里几乎所有可见类的祖先。

## 📖 要点

- **两大本事**：
	- 有==变换==（Transform）——能平移、旋转、缩放。
	- 是==组件容器==——本身像个空壳，靠挂 [[组件 Component]] 决定怎么动、怎么渲染。
- **生命周期**：可以在 Gameplay 代码里==动态生成（Spawn）和销毁（Destroy）==。
- **联网**：支持在网络中复制属性和函数（多人游戏的基础）。
- **继承链位置**：`Object → **Actor** → Pawn → Character`。Actor 在 Object 基础上加了"位置 + 可放世界"。

> [!warning] 易错点
> - **拖进关卡才执行**：Actor 蓝图躺在内容浏览器里不会跑，必须放进世界或被生成。
> - **Actor ≠ 有模型**：很多 Actor 没有可见外形（如出生点、触发盒），靠组件才有外观。

## 连接

- [[GamePlay 框架]] - 本类是整个框架的继承链根基
- [[Pawn]] - 加了"可被操控"的 Actor
- [[Viewport]] - 视口里摆的物体大多是 Actor

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [Actor | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/actors-in-unreal-engine)

## 待深化

- [ ] 补 🗺️ 组件体系（Scene / Primitive / StaticMesh… 组件）
- [ ] 补 ⚙️ C++ 基类 `AActor`、生成与销毁 API
