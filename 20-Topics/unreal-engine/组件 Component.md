---
title: 组件 Component
tags: [UE, GamePlay框架, 组件]
created: 2026-06-02
status: 草稿
---

# 组件 Component

## 一句话定义

> [!abstract]
> 组件 = ==拼装进 [[Actor]] 的"功能块"==。Actor 本身像个空壳，挂什么组件就有什么能力（能动、能渲染、能发声）。挑组件时第一刀先问：==它需不需要"位置"？==

## 📖 要点

| 组件类型 | 有没有位置 | 用来 |
|---|---|---|
| **Actor Component** | ==无位置==·纯功能 | 不需要摆在空间里的逻辑（计分、AI 行为、属性） |
| **Scene Component** | ==有位置==（Transform） | 需要"在哪"的东西（挂点、弹簧臂、相机位置） |
| Primitive Component | 有位置 + 可渲染/碰撞 | 能被看见或碰撞的（网格体、碰撞盒）——是 Scene Component 的子类 |

- ==选择口诀==：需要位置就用 Scene Component，纯功能用 Actor Component。
- **能搭层级**：Scene Component 之间可以父子嵌套，跟着父级一起动（如相机挂在弹簧臂上）。

## 连接

- [[Actor]] - 组件是 Actor 的构成元素，Actor 是组件容器
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-02 - 课程笔记
- [Components | UE 官方文档](https://dev.epicgames.com/documentation/unreal-engine/components-in-unreal-engine)

## 待深化

- [ ] 常用具体组件：StaticMesh / SkeletalMesh / SpringArm / Camera
- [ ] 组件的添加方式（蓝图 AddComponent / C++）
