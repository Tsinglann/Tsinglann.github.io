---
title: '随机热力学与线性响应理论：研究背景'
date: 2026-01-10
permalink: /posts/2026/01/stochastic-thermodynamics-intro/
tags:
  - stochastic thermodynamics
  - linear response theory
  - fluctuation theorem
  - 随机热力学
---

## 研究背景

线性响应理论与涨落定理共同构成了现代非平衡统计物理的基本框架。前者主要回答系统在平衡态附近受到弱扰动时"平均如何响应"的问题，后者则进一步研究系统远离平衡时"随机热力学量如何涨落"的问题。

### 线性响应理论的发展脉络

从 Einstein 关系（1905）到 Onsager 倒易关系（1931），再到 Green–Kubo 公式与涨落–耗散定理（FDT），线性响应理论的核心思想是：**平衡态的涨落决定了系统对外部扰动的线性响应**。

$$\chi(t) = -\frac{1}{k_B T} \frac{d}{dt} C(t), \quad t > 0$$

其中 $\chi(t)$ 是响应函数，$C(t) = \langle A(t) A(0) \rangle_\text{eq}$ 是平衡态自相关函数。

### 涨落定理的进展

涨落定理系列（Evans–Searles 1993、Gallavotti–Cohen 1995、Jarzynski 1997、Crooks 1999）将热力学第二定律从"宏观不等式"推进到了"微观等式"：

$$\frac{P(\Delta S = +\sigma)}{P(\Delta S = -\sigma)} = e^{\sigma / k_B}$$

即正向和反向熵产生的概率之比由玻尔兹曼因子决定。

### 随机热力学框架

Sekimoto（1998）和 Seifert（2005）将热力学量推广到单粒子轨道层面：沿随机轨道 $\{x(t)\}$ 定义功 $W$、热 $Q$、熵产生 $\Delta S$，建立起微观层面的热力学第一、第二定律。

## 研究对象：欠阻尼布朗转子

本论文以欠阻尼朗之万系统为研究对象：

$$I\ddot{\theta} = -\gamma \dot{\theta} + M + \xi(t)$$

其中 $I$ 为转动惯量，$\gamma$ 为阻尼系数，$M$ 为驱动力矩，$\xi(t)$ 为高斯白噪声，满足 $\langle \xi(t)\xi(t') \rangle = 2\gamma k_B T \delta(t-t')$。

选择欠阻尼系统有三个原因：
1. 同时包含惯性项、阻尼项和噪声项，是连接经典随机过程与随机热力学的典型模型
2. 与实验平台（颗粒布朗马达）直接对应
3. 引入磁场控制后可进行主动势场设计，推进到最优控制研究
