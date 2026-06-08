---
title: note6.8 课程大纲
tags: [UE, 课程大纲]
created: 2026-06-08
status: 草稿
---

# note6.8 课程大纲

> 上周做完"能交互的门"，本周让角色活起来：加模型/相机 → 动画蓝图 → 状态机切换。
> 时间为节内相对时间（每节视频各从 00:00 起），按时间顺序排。

## 第 1 节《节点的整理》 `00:00–49:50`

`05:23` 点乘投影到门高度再算夹角（高处才准）
`10:36` 用 Forward 分正反（不是 Right）
`12:10` Sign 取数值符号
`13:20` Select = 蓝图里的 switch
`17:57` 开门方向实时 bug → 开门前先存目标值
`21:33` 节点整理三法：Node(复制) / 函数(真复用) / 宏(多出口)
`45:07` Promote to Variable：拖出即建变量 + set

## 第 2 节《给角色添加模型》 `00:00–50:09`

`01:38` 第一人称两套模型：Only Owner See(自己看) / Owner No See(别人看)
`06:50` 加 Skeletal Mesh
`08:56` 绕 Z 转 -90 对齐前向
`09:27` 下移 -88/-96 贴地
`22:25` 加相机：普通相机 vs Cine Camera
`25:36` 相机挂 head 骨骼 Socket
`33:06` Camera Mesh Hidden in Game：游戏里看见相机
`36:14` FOV 视野角：大=广角物小，小=长焦拉近
`44:50` 待验证 — Can Character Step Up On（能否踏上去，老师没调清）

## 第 3 节《创建动画蓝图》 `00:00–49:42`

`07:59` 双模型渲染：Only Owner See
`10:35` First Person Primitive
`15:18` 关阴影 Cast Shadow（自己看的模型用别人那套投影）
`17:19` 创建动画蓝图(选骨骼)；AnimGraph 出动作 / EventGraph 取数据
`22:09` Blend Pose by bool / by int + 过渡时间
`29:54` 取拥有者 → Cast 角色 → 存 CharacterMovement（只初始化 Cast 一次）
`38:10` isMoving = 水平速度 Vector Length XY > 阈值
`44:22` IsFalling 判断是否在空中

## 第 4 节《动画状态机》 `00:00–49:46`

`01:55` IsValid / Convert to Validated Get（判引用有效，值类型不能判）
`06:22` Sequence：顺序但同步、不等上一步；防长逻辑中断
`11:40` 坑：for 底层是 Sequence → 别在 for/Sequence 用 Delay
`28:31` 状态机：状态 + 转换条件 + 默认状态 + Loop Animation
`29:39` Motion Matching（仅提及）
`42:52` 官方多状态机：Locomotion + 跳跃(起跳→下落 loop→落地)

## 串联

门能交互 → 给角色加身体+相机 → 动画蓝图读速度/是否下落 → 状态机切 Idle/Walk。角色从透明胶囊变成像个游戏角色。

## 链接

- [[UE 学习地图]]
- 动画系统：[[动画系统]] · [[骨骼与 Skeletal Mesh]] · [[动画蓝图]] · [[动画混合 Blend Pose]] · [[动画状态机 State Machine]]
- 角色/相机：[[第一人称角色与相机]]
- 蓝图基础：[[节点整理]] · [[Sequence]] · [[IsValid 判断有效]]
- 补充已有：[[向量判断方位]] · [[Delay 延迟]]
