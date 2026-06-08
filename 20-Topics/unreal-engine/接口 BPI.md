---
title: 接口 BPI（Blueprint Interface）
aliases: [BPI, Blueprint Interface]
tags: [UE, 蓝图通信]
created: 2026-06-07
status: 草稿
---

# 接口 BPI（Blueprint Interface）

## 一句话定义

> [!abstract]
> 蓝图接口（BPI）= ==一份"消息合同"==，只定义函数签名、不写逻辑。约定"任何实现我的对象，都保证有这个函数"。用来让蓝图之间**沟通而不互相 [[类型转换 Cast\|Cast]]**——解耦。

## 📖 要点

### 创建与实现

![[Pasted image 20260605102221.png]]

1. **创建**：内容浏览器右键 → 蓝图 → **蓝图接口(Blueprint Interface)**，在里面定义函数（如 `Interact`）。
2. **谁来实现**：在目标蓝图（如 BP_door）`Class Settings → Interfaces → Add` 加上这个接口。

![[Pasted image 20260605102303.png]]

3. **实现函数**：左边 My Blueprint 的 **Interfaces 区**会出现该函数，双击实现它（接你的开关门逻辑）。

![[Pasted image 20260605102316.png]]

### 接口函数的 Input / Output

- **Input**：调用方==随消息传给实现方的数据==。例：`Interact(interactor)`，`interactor` = 谁在交互（玩家传 self）→ 门就知道是谁开的。
- **Output**：实现方==返回给调用方的数据==（如"成功了吗"）。
- ==有 Output → 实现为函数；无 Output → 可实现为[[自定义事件 CustomEvent\|自定义事件]]==（更简单）。

### 调用（关键细节）

> [!tip] 用 Message 版调用
> 调用时选紫色信封图标的 **`Interact (Message)`** 版本，`Target` = 对方 actor。==对方没实现接口就静默忽略，不报错==——这才是"对谁都能喊"的安全调用。

## 📖 为什么用 BPI（对比 Cast）

| | [[类型转换 Cast]] | 接口 BPI |
|---|---|---|
| 调用方要知道对方具体类吗 | 要 | ==不要==（只要"实现了接口"） |
| 加一种新可交互物 | 再 Cast 一个类，节点爆炸 | ==零改动==，新物体实现同一接口即可 |

> ==玩家只喊一句 "Interact！"，谁实现了接口谁自己响应==——门、箱子、NPC 通吃。这就是"Cast 太多就用接口"的真正含义。

## 连接

- [[类型转换 Cast]] - 它要解决的"耦合"问题
- [[自定义事件 CustomEvent]] - 无 Output 的接口函数用事件实现
- [[GamePlay 框架]] - 总览

## 来源

- 2026-06-05 - 课程笔记（第二节·接口 BPI）

## 待深化

- [ ] BPI vs Event Dispatcher 的取舍（凑齐就建「蓝图通信」文件夹）
- [ ] 带返回值的接口函数实现实例
