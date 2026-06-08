---
title: GamePlay 框架
tags: [UE, GamePlay框架, 总览]
created: 2026-06-02
status: 草稿
---

# GamePlay 框架

## 一句话定义

> [!abstract]
> GamePlay 框架 = UE 内置的一套"游戏运转骨架"。它用一堆固定职责的类，回答两个问题：**谁基于谁（继承链）** 和 **运行时谁管谁（层级）**。看懂这两条线，框架就不再是一堆名词。

## 🗺️ 知识图谱

<svg viewBox="0 0 960 440" xmlns="http://www.w3.org/2000/svg" font-family="'Segoe UI','Microsoft YaHei',sans-serif">
  <defs>
    <marker id="gp-ar" markerWidth="9" markerHeight="9" refX="7" refY="4" orient="auto"><path d="M0 0 L9 4 L0 8 z" fill="#94a3b8"/></marker>
    <marker id="gp-arc" markerWidth="9" markerHeight="9" refX="7" refY="4" orient="auto"><path d="M0 0 L9 4 L0 8 z" fill="#0e7490"/></marker>
  </defs>
  <text x="20" y="22" font-size="13" fill="#64748b">GamePlay 框架 · 两条主线</text>

  <!-- ① 继承链 -->
  <text x="50" y="56" font-size="14" font-weight="700" fill="#0c4a6e">① 继承链（谁基于谁）</text>
  <g text-anchor="middle">
    <rect x="70" y="72" width="180" height="52" rx="10" fill="#1e293b"/>
    <text x="160" y="96" font-size="15" font-weight="700" fill="#ffffff">Object</text>
    <text x="160" y="114" font-size="11" fill="#cbd5e1">最基础的类</text>

    <rect x="70" y="176" width="180" height="52" rx="10" fill="#0e7490"/>
    <text x="160" y="200" font-size="15" font-weight="700" fill="#ffffff">Actor</text>
    <text x="160" y="218" font-size="11" fill="#e0f2fe">+位置 · 可放进世界</text>

    <rect x="70" y="280" width="180" height="52" rx="10" fill="#0e7490"/>
    <text x="160" y="304" font-size="15" font-weight="700" fill="#ffffff">Pawn</text>
    <text x="160" y="322" font-size="11" fill="#e0f2fe">+可被操控</text>

    <rect x="70" y="384" width="180" height="52" rx="10" fill="#0e7490"/>
    <text x="160" y="408" font-size="15" font-weight="700" fill="#ffffff">Character</text>
    <text x="160" y="426" font-size="11" fill="#e0f2fe">+运动组件</text>
  </g>
  <g stroke="#94a3b8" stroke-width="2.5" fill="none" marker-end="url(#gp-ar)">
    <path d="M160 124 V170"/>
    <path d="M160 228 V274"/>
    <path d="M160 332 V378"/>
  </g>

  <!-- ② 运行时层级 -->
  <text x="500" y="56" font-size="14" font-weight="700" fill="#9a3412">② 运行时层级（谁管谁）</text>
  <g text-anchor="middle">
    <rect x="540" y="72" width="240" height="50" rx="10" fill="#7c2d12"/>
    <text x="660" y="94" font-size="15" font-weight="700" fill="#ffffff">GameMode</text>
    <text x="660" y="112" font-size="11" fill="#fed7aa">加载地图时生成 · 定玩法规则</text>
  </g>
  <g text-anchor="start">
    <rect x="560" y="152" width="220" height="44" rx="8" fill="#fff7ed" stroke="#fb923c" stroke-width="1.5"/>
    <text x="574" y="172" font-size="13" font-weight="700" fill="#9a3412">GameState</text>
    <text x="574" y="188" font-size="10" fill="#b45309">全局信息：比分 / 目标</text>

    <rect x="560" y="208" width="220" height="44" rx="8" fill="#fff7ed" stroke="#fb923c" stroke-width="1.5"/>
    <text x="574" y="228" font-size="13" font-weight="700" fill="#9a3412">PlayerController</text>
    <text x="574" y="244" font-size="10" fill="#b45309">操控玩家（同时唯一）</text>

    <rect x="560" y="264" width="220" height="44" rx="8" fill="#fff7ed" stroke="#fb923c" stroke-width="1.5"/>
    <text x="574" y="284" font-size="13" font-weight="700" fill="#9a3412">PlayerState</text>
    <text x="574" y="300" font-size="10" fill="#b45309">玩家信息：血量 / 物品</text>

    <rect x="560" y="320" width="220" height="44" rx="8" fill="#fff7ed" stroke="#fb923c" stroke-width="1.5"/>
    <text x="574" y="340" font-size="13" font-weight="700" fill="#9a3412">HUD</text>
    <text x="574" y="356" font-size="10" fill="#b45309">屏幕 UI</text>

    <rect x="822" y="208" width="120" height="44" rx="8" fill="#ecfeff" stroke="#0e7490" stroke-width="1.5"/>
    <text x="836" y="228" font-size="13" font-weight="700" fill="#0e7490">Pawn</text>
    <text x="836" y="244" font-size="10" fill="#0e7490">模型 + 相机</text>
  </g>
  <!-- 树干在方块左侧外缘 (x=540) + 分支伸入 -->
  <g stroke="#fb923c" stroke-width="2.5" fill="none">
    <path d="M540 122 V342"/>
    <path d="M540 174 H560"/>
    <path d="M540 230 H560"/>
    <path d="M540 286 H560"/>
    <path d="M540 342 H560"/>
  </g>
  <!-- PlayerController 操控 Pawn -->
  <text x="788" y="224" font-size="10" fill="#0e7490">操控</text>
  <g stroke="#0e7490" stroke-width="2.5" fill="none" marker-end="url(#gp-arc)">
    <path d="M780 230 H818"/>
  </g>
</svg>

> [!info] 两条线别混
> **继承链**讲"血统"——Character *是一种* Pawn *是一种* Actor。**运行时层级**讲"分工"——PlayerController *操控* 一个 Pawn，GameMode *管着* 全场。同一个类（如 Pawn）会同时出现在两条线上，但说的是两件事。

## ⚡ 使用方法

### 类速查表

| 类              | 一句话职责               | 详情                    |
| -------------- | ------------------- | --------------------- |
| **Actor**      | 能放进世界的一切（有位置、是组件容器） | [[Actor]]             |
| **Pawn**       | 能被玩家/AI 操控的 Actor   | [[Pawn]]              |
| **Character**  | 会走跑跳的特殊 Pawn        | [[Character]]         |
| **Controller** | 非实体，负责操控 Pawn       | [[Controller]]        |
| **GameMode**   | 定规则、决定用哪些类、加载时生成    | [[GameMode]]          |
| GameState      | 全局游戏信息（比分、目标）       | [[GameState]]         |
| PlayerState    | 单个玩家信息（血量、物品）       | [[PlayerState]]       |
| HUD            | 屏幕上的 UI 元素          | [[HUD]]               |
| World          | 地图最上层容器，万物存于其中      | [[World]]             |
| GameInstance   | 跨关卡常驻，整局生命周期不变      | [[GameInstance]]      |

> 官方全表见来源链接，这里只列常用的。

### 设置 GameMode

**默认 GameMode**（整个项目）

![[Pasted image 20260602230940.png]]

- `项目设置 → Maps & Modes → Default GameMode` 选择项目级默认。

**为单个 Level 单独设置**

![[Pasted image 20260602231008.png]]
![[Pasted image 20260602231019.png]]

- 打开关卡 → `World Settings → GameMode Override` → 这张地图用专属规则，覆盖项目默认。

## 📖 教学（核心原理）

### 1. 框架到底解决什么

- **本质**：UE 替你预写好"一局游戏怎么跑"的骨架——玩家从哪生、谁记分、UI 谁画，都有专门的类。
- **你的活**：往这些类里填自己的逻辑，而不是从零造轮子。
- ==看框架先抓两条线：继承链 + 运行时层级。==

### 2. 继承链：每层"加一样东西"

> [!tip] 主线记法
> ==Object → Actor → Pawn → Character，每往下一层只加一个能力。==

| 类 | 在上一层基础上加了 | 于是能 |
|---|---|---|
| **Object** | —（最基础） | 啥都还不能，纯数据 |
| **Actor** | 位置 / 变换 + 组件容器 | 被放进世界、移动旋转缩放 |
| **Pawn** | 可被 Controller 操控 | 被玩家或 AI 接管 |
| **Character** | 运动组件（CharacterMovement） | 走、跑、跳、游泳 |

- 选父类时（截图那个 Pick Parent Class），就是在这条链上挑起点：做静物选 Actor，做能控制的角色选 Pawn/Character。

### 3. 运行时层级：GameMode 是总指挥

- ==加载地图 → 先生成 GameMode，它再决定生成哪些类。==
- 关键分工（别记混）：
	- **GameMode**：定规则、决定用哪套类（玩法的"宪法"）。
	- **PlayerController**：操控玩家，==同一时刻只有一个==。
	- **Pawn**：可以有多个（一堆角色），但一个 Controller 同时只控一个。
	- **GameState vs PlayerState**：前者记==全局==（比分），后者记==单个玩家==（血量/物品）。

### 4. 为什么蓝图要放到世界上才执行

- ==代码（蓝图）必须先被"生成"成实例，才会运行。==
- 所以一个 Actor 蓝图，**拖进关卡**（或被 GameMode 生成）后才执行；只躺在内容浏览器里不会跑。
- 这也是为什么 GameMode/Controller 这些"管理类"要靠"加载地图"这个时机自动生成。

> [!warning] 易错点
> - **把继承链当成运行时关系** → "谁是谁"≠"谁管谁"，两条线分开看。
> - **蓝图不执行** → 没放进世界 / 没被生成；拖进关卡或由 GameMode 生成。
> - **想让单张地图用特殊规则** → 用 `World Settings` 的 GameMode Override，别改项目默认。
> - **以为能同时操控多个 Pawn** → 一个 PlayerController 同时只控一个，需切换 Possess。

> [!question]- 我的疑问
> （跟课 / 动手时冒出的问题记这里）

## 连接

- [[Viewport]] - 视口里摆的物体大多是 [[Actor]]，归 GamePlay 框架管
- [[Actor]] / [[Pawn]] / [[Character]] / [[Controller]] / [[GameMode]] - 框架核心类，从本篇拆出
- [[UMG]] - HUD / UI 系统（待创建）

## 来源

- 2026-06-02 - 课程笔记（GamePlay 框架）
- [虚幻引擎中的 Gameplay 框架 | UE 5.7 官方文档](https://dev.epicgames.com/documentation/unreal-engine/gameplay-framework-in-unreal-engine?lang=zh-CN)

## 待深化

- [x] World / GameInstance / GameState / PlayerState / HUD 各自拆成原子笔记
- [ ] 网络联机相关：NetworkManager、Session（多人时回头补）
- [ ] 补 ⚙️ C++ 对应基类（UObject / AActor / APawn…，蓝图熟悉后再回头）
