---
title: '可编程磁场控制与布朗卡诺热机'
date: 2026-03-20
permalink: /posts/2026/03/magnetic-control-brownian-carnot/
tags:
  - Brownian Carnot engine
  - magnetic control
  - optimal transport
  - stochastic thermodynamics
  - 布朗热机
  - 磁场控制
---

## 动机：从被动观测到主动调控

传统振动驱动颗粒布朗马达平台通过振动强度控制有效温度，但**无法独立操控势能景观**。若能引入可编程外场，就可以：
1. 构造任意形状的势阱（调谐弹簧常数、非对称棘轮势等）
2. 在粒子运动过程中动态改变势场，实现有限时间热力学最优过程
3. 设计布朗热机循环

## 多线圈电磁铁阵列的逆源设计

### 物理模型

将工作区域内的磁场分布 $B(x)$ 用线圈电流 $\{I_j\}$ 线性展开：

$$B(x_i) = \sum_j A_{ij} I_j$$

其中响应矩阵 $A_{ij}$ 由偶极近似（或 Biot–Savart 积分）计算。给定目标磁场分布 $B^\ast(x_i)$，求解最优电流组合：

$$\min_{\{I_j\}} \sum_i \left[ B(x_i) - B^\ast(x_i) \right]^2 + \lambda \sum_j I_j^2$$

后一项为 **Tikhonov 正则化**，抑制病态解。

### 空间带宽限制

由于线圈数量有限，磁场的空间分辨率受限。高频空间成分（短波长势场细节）无法精确重建——这与信号处理中的 Gibbs 现象类似：截断有限阶 Fourier 级数会在间断点附近出现振荡。

### 硬件方案

- 驱动芯片：PCA9685（16 路 PWM）+ L298N H桥
- 传感器：SS49E 霍尔传感器（PID 闭环校正磁滞效应）
- 控制器：Arduino

## 仿真结果

<div style="display:flex;gap:1em;flex-wrap:wrap;justify-content:center;margin:1.5em 0;">
  <div style="text-align:center;">
    <img src="/images/research/mode1_shape_5__A_1_5_k_BT.png" alt="Step potential" style="max-width:280px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <figcaption style="font-size:0.85em;color:#666;">阶跃磁势场（目标与重建对比）</figcaption>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/mode2_shape5.png" alt="Ratchet" style="max-width:280px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <figcaption style="font-size:0.85em;color:#666;">非对称棘轮势 $V(\theta)=\sin 3\theta + 0.5\sin(6\theta+\pi/4)$</figcaption>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/mode3_multi_shape.png" alt="Multi shape" style="max-width:280px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <figcaption style="font-size:0.85em;color:#666;">多种势场形状叠加</figcaption>
  </div>
</div>

## 布朗卡诺热机设计

利用可编程势阱，可以实现颗粒布朗卡诺循环：

| 过程 | 操作 | 热力学对应 |
|------|------|-----------|
| 等温膨胀 | 缓慢释放势阱（$\kappa \searrow$），与热浴 $T_H$ 接触 | 系统做功，吸热 |
| 绝热冷却 | 快速绝热切换，等效温度 $T_H \to T_C$ | 等熵压缩 |
| 等温压缩 | 缓慢收紧势阱（$\kappa \nearrow$），与冷浴 $T_C$ 接触 | 外界做功，放热 |
| 绝热加热 | 快速绝热切换，等效温度 $T_C \to T_H$ | 等熵膨胀 |

理想情况下效率达到卡诺效率 $\eta_C = 1 - T_C/T_H$。欠阻尼惯性效应使实际效率略低，功率则在有限时间循环中有所提升。

## 其他应用前景

- **有限时间最优输运**：在时间 $\tau$ 内将粒子分布从 $\rho_0$ 输运到 $\rho_1$，最小化熵产生。最优协议满足 Wasserstein 距离的 $1/\tau$ 标度关系。
- **Landauer 信息擦除**：双势阱系统，通过磁场控制实现比特重置，验证 Landauer 原理的热力学下界 $k_B T \ln 2$。
