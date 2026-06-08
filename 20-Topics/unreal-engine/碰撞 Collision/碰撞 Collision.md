---
title: 碰撞 Collision
tags: [UE, 碰撞, 总览]
created: 2026-06-04
status: 草稿
---

# 碰撞 Collision

## 一句话定义

> [!abstract]
> 碰撞系统回答一件事：==两个东西碰到一起时会发生什么==。先定"碰撞关系"（忽略/重叠/阻挡），再分两种用法——**主动检测**（我主动发射线去问"碰到啥了"）和**被动检测**（等别人撞我、事件自动来）。

## 🗺️ 知识图谱

<svg viewBox="0 0 880 380" xmlns="http://www.w3.org/2000/svg" font-family="'Segoe UI','Microsoft YaHei',sans-serif">
  <text x="20" y="20" font-size="13" fill="#64748b">碰撞 Collision · 知识脉络</text>
  <g stroke="#94a3b8" stroke-width="2" fill="none">
    <path d="M195 195 C 235 195, 235 70, 275 70"/>
    <path d="M195 195 C 235 195, 235 185, 275 185"/>
    <path d="M195 195 C 235 195, 235 300, 275 300"/>
  </g>
  <rect x="40" y="165" width="155" height="60" rx="12" fill="#1e293b"/>
  <text x="117" y="193" font-size="16" font-weight="700" fill="#ffffff" text-anchor="middle">碰撞</text>
  <text x="117" y="213" font-size="11" fill="#cbd5e1" text-anchor="middle">碰到一起会怎样</text>
  <g>
    <rect x="275" y="44" width="200" height="52" rx="10" fill="#fee2e2" stroke="#dc2626" stroke-width="1.5"/>
    <text x="288" y="68" font-size="14" font-weight="700" fill="#991b1b">① 三种关系</text>
    <text x="288" y="87" font-size="11" fill="#7f1d1d">Ignore 忽略 / Overlap 重叠 / Block 阻挡</text>

    <rect x="275" y="159" width="200" height="52" rx="10" fill="#dcfce7" stroke="#16a34a" stroke-width="1.5"/>
    <text x="288" y="183" font-size="14" font-weight="700" fill="#166534">② 主动检测 Trace</text>
    <text x="288" y="202" font-size="11" fill="#15803d">我主动发射线去"问"</text>
    <text x="500" y="190" font-size="12" fill="#475569">→ [[主动碰撞检测 Trace]]</text>

    <rect x="275" y="274" width="200" height="52" rx="10" fill="#dbeafe" stroke="#2563eb" stroke-width="1.5"/>
    <text x="288" y="298" font-size="14" font-weight="700" fill="#1e3a8a">③ 被动检测 事件</text>
    <text x="288" y="317" font-size="11" fill="#1e40af">被撞到，事件自动触发</text>
    <text x="500" y="305" font-size="12" fill="#475569">→ [[被动碰撞检测 事件]]</text>
  </g>
</svg>

## 📖 教学（核心原理）

### 1. 三种碰撞关系（最基础）

> 每个物体对每条"通道/对象类型"都设一个响应：

![[Pasted image 20260604091237.png]]

| 关系 | 效果 | 触发的事件 |
|---|---|---|
| **Ignore** 忽略 | 完全无视，直接穿过 | 无 |
| **Overlap** 重叠 | 能穿过，但进/出会报告 | `BeginOverlap` / `EndOverlap` |
| **Block** 阻挡 | 物理挡住，撞上停住 | `Hit` |

> [!tip] 谁说了算（关键规则）
> ==优先级：Ignore > Overlap > Block。== 要"阻挡"必须**双方都设 Block**；只要一方是 Overlap（且无人 Ignore）就是 Overlap；任一方 Ignore 就互相穿过。

### 2. 还有个开关：Collision Enabled

- **No Collision**：彻底关掉。
- **Query Only（仅查询）**：只参与"检测/重叠"，不做物理碰撞——==做触发器、做 Trace 检测用这个==。
- **Physics Only**：只做物理，不响应查询。
- **Query and Physics**：两者都开（既能挡又能被检测）。

### 3. 主动 vs 被动（本篇总纲）

- ==主动 = 我问==：在某个时机（开火、交互）主动发射一条 Trace 去查"路径上碰到什么"。→ [[主动碰撞检测 Trace]]
- ==被动 = 等通知==：我啥也不做，别人撞到/重叠我时，引擎自动调用我的事件。→ [[被动碰撞检测 事件]]

### 4. 用蓝图设置碰撞

![[Pasted image 20260604091332.png]]

- 运行时改：`Set Collision Enabled`、`Set Collision Response to Channel/All Channels`、`Set Collision Profile Name`。
- 这正是你做"按 F 切 Overlap/Block"用到的节点。

> [!question]- 我的疑问
> （跟课 / 动手时冒出的问题记这里）

## 连接

- [[组件 Component]] - 碰撞挂在组件上（Primitive Component 才有碰撞）
- [[主动碰撞检测 Trace]] / [[被动碰撞检测 事件]] - 两种用法
- [[输入系统/角色移动与视角控制\|角色移动]] - 移动也依赖碰撞阻挡

## 来源

- 2026-06-04 - 课程笔记（碰撞）

## 待深化

- [ ] 碰撞通道（Collision Channel）自定义
- [ ] 碰撞预设（Profile）的管理
