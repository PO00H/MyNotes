---
title: Viewport（视口）
tags: [UE, 编辑器, 视口]
created: 2026-06-02
status: 草稿
---

# Viewport（视口）

## 一句话定义

> [!abstract]
> 视口 = 你在 UE 编辑器里观察和操作 3D 世界的那扇**窗**。核心就两件事——**移动"我的眼睛"(导航)** 和 **移动"世界里的物体"(变换)**。新手第一关就是别把这两个搞混。

## 🗺️ 知识图谱

<svg viewBox="0 0 880 540" xmlns="http://www.w3.org/2000/svg" font-family="'Segoe UI', 'Microsoft YaHei', sans-serif">
  <text x="24" y="18" font-size="13" fill="#64748b">Viewport 视口 · 知识脉络</text>
  <g stroke="#94a3b8" stroke-width="2" fill="none">
    <path d="M 184 266 C 217 266, 217 53, 250 53"/>
    <path d="M 184 266 C 217 266, 217 141, 250 141"/>
    <path d="M 184 266 C 217 266, 217 229, 250 229"/>
    <path d="M 184 266 C 217 266, 217 317, 250 317"/>
    <path d="M 184 266 C 217 266, 217 405, 250 405"/>
    <path d="M 184 266 C 217 266, 217 493, 250 493"/>
  </g>
  <rect x="24" y="234" width="160" height="64" rx="12" fill="#1e293b"/>
  <text x="104" y="262" font-size="17" font-weight="700" fill="#ffffff" text-anchor="middle">Viewport</text>
  <text x="104" y="284" font-size="12" fill="#cbd5e1" text-anchor="middle">视口 = 你的眼睛</text>
  <g>
    <rect x="250" y="30" width="172" height="46" rx="10" fill="#e0f2fe" stroke="#0284c7" stroke-width="1.5"/>
    <text x="262" y="59" font-size="14" font-weight="700" fill="#0c4a6e">① 导航操作</text>
    <text x="442" y="48" font-size="12" fill="#475569">右键+WASD 飞行 · Alt+左键 环绕</text>
    <text x="442" y="66" font-size="12" fill="#475569">中键 平移 · 滚轮 缩放 · F 聚焦</text>

    <rect x="250" y="118" width="172" height="46" rx="10" fill="#e0f2fe" stroke="#0284c7" stroke-width="1.5"/>
    <text x="262" y="147" font-size="14" font-weight="700" fill="#0c4a6e">② 变换 Gizmo</text>
    <text x="442" y="136" font-size="12" fill="#475569">W 移动 · E 旋转 · R 缩放</text>
    <text x="442" y="154" font-size="12" fill="#475569">World ⇄ Local 坐标系切换</text>

    <rect x="250" y="206" width="172" height="46" rx="10" fill="#e0f2fe" stroke="#0284c7" stroke-width="1.5"/>
    <text x="262" y="235" font-size="14" font-weight="700" fill="#0c4a6e">③ 视图模式</text>
    <text x="442" y="224" font-size="12" fill="#475569">Lit 光照 · Unlit 无光</text>
    <text x="442" y="242" font-size="12" fill="#475569">Wireframe 线框 · 光照细节</text>

    <rect x="250" y="294" width="172" height="46" rx="10" fill="#e0f2fe" stroke="#0284c7" stroke-width="1.5"/>
    <text x="262" y="323" font-size="14" font-weight="700" fill="#0c4a6e">④ 视角类型</text>
    <text x="442" y="312" font-size="12" fill="#475569">透视 Perspective</text>
    <text x="442" y="330" font-size="12" fill="#475569">正交:顶 / 前 / 侧 视图</text>

    <rect x="250" y="382" width="172" height="46" rx="10" fill="#e0f2fe" stroke="#0284c7" stroke-width="1.5"/>
    <text x="262" y="411" font-size="14" font-weight="700" fill="#0c4a6e">⑤ 显示标志</text>
    <text x="442" y="400" font-size="12" fill="#475569">Show Flags:网格/碰撞/光照</text>
    <text x="442" y="418" font-size="12" fill="#475569">控制视口"显示什么"</text>

    <rect x="250" y="470" width="172" height="46" rx="10" fill="#e0f2fe" stroke="#0284c7" stroke-width="1.5"/>
    <text x="262" y="499" font-size="14" font-weight="700" fill="#0c4a6e">⑥ 运行测试</text>
    <text x="442" y="488" font-size="12" fill="#475569">PIE 播放 ▶ · Simulate 模拟</text>
    <text x="442" y="506" font-size="12" fill="#475569">Eject 脱离 Pawn 控制</text>
  </g>
</svg>

## ⚡ 使用方法

> [!tip] 速查心法
> 日后秒查就看这一段。**导航靠右键，变换靠 W / E / R——这两组练成肌肉记忆，视口就通了。**

**导航(按住右键时)**

| 操作 | 效果 |
|---|---|
| 右键 + `W/A/S/D` | 前/左/后/右 飞行 |
| 右键 + `E` / `Q` | 上升 / 下降 |
| 右键 + 移动鼠标 | 转动视角 |
| 滚轮上下 | 拉近 / 拉远 |
| `Alt` + 左键拖 | 绕选中物体环绕(看模型用) |
| 鼠标中键拖 | 平移视图 |
| 选中物体按 `F` | 聚焦,把它居中 |
| 右键拖时滚动滚轮 | 调飞行速度 |

**变换工具(Gizmo)**

| 快捷键 | 工具 |
|---|---|
| `W` | 移动 Move |
| `E` | 旋转 Rotate |
| `R` | 缩放 Scale |
| `空格` | 在 移动/旋转/缩放 间循环切换 |
| 工具栏地球/方块图标 | World(世界)⇄ Local(自身)坐标系 |
| `End` | 把物体吸附贴到地面 |

**视图模式 / 视角**

| 操作 | 效果 |
|---|---|
| 左上「透视」下拉 | 切 透视 / 顶 / 前 / 侧 视图(正交) |
| 左上「Lit」下拉 | Lit 带光照 / Unlit 纯色 / Wireframe 线框 / 光照细节 |
| `G` 键 | Game View，临时隐藏编辑器图标，看"玩家视角"纯净画面 |

**运行测试**

| 操作 | 效果 |
|---|---|
| `▶ Play`(或 `Alt+P`) | 在视口里试玩(PIE = Play In Editor) |
| `Esc` / 再点停止 | 退出试玩 |
| `Shift+F1` | 试玩中找回鼠标指针 |

## 📖 教学(核心原理)

### 1. 视口到底是什么

- **本质**：编辑器里看 3D 世界的那扇窗——摆放、观察、调试关卡的==工作台==。
- **不是**：游戏本身。
- **新手第一关**：分清你在动 **眼睛(导航)** 还是动 **物体(变换)**。

### 2. 导航：右键是核心

- ==按住右键 = 飞行模式==：这时 `WASD` 才能飞，松开就失效。
- **为什么**：关卡可能几公里大，飞过去最快。
- **两种看法别混**：
	- 右键 → "我在世界里飞"
	- `Alt`+左键 → "我绕着物体转圈看"（检查单个模型）

### 3. 变换：坐标系是关键

- **Gizmo**：选中物体后的三色操纵杆——`W` 移 / `E` 转 / `R` 缩。
- **World vs Local**（最容易卡的点）：

| 坐标系 | 箭头朝向 | 什么时候用 |
|---|---|---|
| **World** 世界 | 永远指世界固定方向 | 默认、沿世界轴移动 |
| **Local** 自身 | 跟着物体自己的朝向 | ==摆斜着的物体== |

> 🚗 斜停的车：Local 下"前"=车头方向，World 下"前"=世界正前方。

### 4. 视图模式：换种"看法"排查问题

| 模式 | 看到什么 | 用来 |
|---|---|---|
| **Lit** | 正常带光照 | 日常 |
| **Unlit** | 只看物体本色 | 画面太暗 → 分清"灯没打好"还是"模型本身黑" |
| **Wireframe** | 只看网格线 | 查面数、穿模 |

> [!tip] 调试心法
> 画面不对，==先换视图模式定位是光照还是模型问题，别瞎调。==

### 5. 透视 vs 正交

- **透视**（默认）：近大远小，像人眼。
- **正交**（顶/前/侧）：无变形，适合==精确对齐==（严丝合缝拼物体）。

### 6. PIE：随时按 ▶ 试玩

- ==不用打包就能玩==：点 `▶ Play` 直接进游戏(PIE)，`Esc` 退出。
- 学蓝图后的高频循环：**改 → Play → 看 → 再改**。

> [!warning] 易错点
> - **WASD 不动** → 没按住右键
> - **飞太快 / 太慢** → 按住右键时滚滚轮调速
> - **拖物体却整个视角在转** → 你按的是右键；先左键选中再用 Gizmo
> - **移动方向很怪** → 在 Local 坐标系；切回 World
> - **试玩后鼠标消失** → `Shift+F1` 找回，或 `Esc` 停止

> [!question]- 我的疑问
> （跟课 / 动手时冒出的问题记这里）

## 连接

- [[GamePlay 框架]] - 视口里摆的物体大多是 [[Actor]]，归 GamePlay 框架管
- 内容浏览器 / 项目结构 - 同属"编辑器与项目"基础(待创建)

## 来源

- 2026-06-02 - 课程笔记(Viewport 与 GamePlay 框架)

## 待深化

- [ ] 补 ⚙️ C++ / 反射相关(蓝图熟悉后再回头)
- [ ] 视口书签、多视口分屏等进阶操作
