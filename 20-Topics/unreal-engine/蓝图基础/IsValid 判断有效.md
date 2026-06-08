---
title: IsValid 判断有效
tags: [UE, 蓝图基础]
created: 2026-06-08
status: 草稿
---

# IsValid 判断有效

## 一句话定义

> [!abstract]
> 判断一个==引用类型是否有效（非空）==。常用前先判一手，避免空引用报错（"Accessed None"）。

## 📖 要点

- **两种写法**：
	- `IsValid` 节点 + `Branch`：经典，但要两个节点。
	- ==从引脚拖出 → 右键 `Convert to Validated Get`==：一步到位，官方常用，不用额外接节点。
- **只对引用类型有效**：[[变量类型|Object/引用类型]]（角色、组件…）才能判断有效无效；==[[数值类型|值类型]]（int/float/bool）没有"无效"概念，永远有效==，不能判断。

![[Pasted image 20260608223242.png]]

> [!tip] 实战
> 动画蓝图里 `Update` 前先 `Convert to Validated Get` 判断 `CharacterMovement` 有效，再读速度——拿不到就跳过，不报错。（见 [[动画蓝图]]）

## 连接

- [[蓝图基础]] - 所属（枢纽）
- [[类型转换 Cast]] - Cast 失败也会得到无效引用，配合判断
- [[变量类型]] - 引用类型 vs 值类型
- [[动画蓝图]] - 取拥有者后判有效

## 来源

- 2026-06-08 - note6.8（动画状态机）

## 待深化

- [ ] IsValid 与 `?` 节点、Is Valid Index 的区别
