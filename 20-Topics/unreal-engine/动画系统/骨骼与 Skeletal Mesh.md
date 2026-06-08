---
title: 骨骼与 Skeletal Mesh
tags: [UE, 动画系统]
created: 2026-06-08
status: 草稿
---

# 骨骼与 Skeletal Mesh

## 一句话定义

> [!abstract]
> **Skeletal Mesh（骨骼网格体）= 带骨架、能做动画的模型**；**Skeleton（骨骼）= 它的骨架**，动画就绑在骨骼上。**Socket（插槽）= 骨骼上的挂点**，用来挂相机、武器等。

## 📖 要点

- **Skeletal Mesh vs [[组件 Component|Static Mesh]]**：静态网格不会动；骨骼网格有骨架，能播放动画。
- **骨骼共享**：同一套骨骼（如官方 Mannequin 男/女）可共用动画——动画绑定的是**骨骼**不是模型。
- **加角色模型**（note6.8 实操）：
	- 给角色加一个 Skeletal Mesh 组件，绕 Z 转 `-90` 对齐前方向。
	- 下移到 `-88`/`-96`（与胶囊体半高一致）让脚贴地。
- **Socket 插槽**：在骨骼某个骨头上设挂点。例：相机挂到 `head` 骨骼，武器挂到手部骨骼。打开骨骼资产 → Bones → 选 `Show All Bones` 找名字（如 head）。

> [!tip] 怎么找骨骼名
> 打开 Skeletal Mesh 的骨骼资产，骨骼列表里 `head`=头、`spine`=胸腔、手臂往手处点能高亮——官方模板命名规范。

## 连接

- [[动画系统]] - 所属（枢纽）
- [[动画蓝图]] - 动画蓝图选的就是骨骼
- [[第一人称角色与相机]] - 相机就挂在 head Socket
- [[Character]] - 角色自带一个 Mesh 槽

## 来源

- 2026-06-08 - note6.8（给角色添加模型）

## 待深化

- [ ] 武器挂手部 Socket 的实操
- [ ] 骨骼重定向 Retarget（换模型复用动画）
