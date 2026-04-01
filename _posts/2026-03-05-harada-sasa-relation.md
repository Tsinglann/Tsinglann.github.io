---
title: 'Harada–Sasa 关系：自由 OU 过程的"平凡非平衡稳态"'
date: 2026-03-05
permalink: /posts/2026/03/harada-sasa-relation/
tags:
  - Harada-Sasa
  - power spectrum
  - FDT
  - NESS
  - 谱耗散
  - 非平衡稳态
---

## Harada–Sasa 关系

Harada 与 Sasa（2005）提出，对于稳态系统，能量耗散率可通过速度功率谱与 FDT 的"违反量"来估计：

$$\dot{W} = \int_{-\infty}^{+\infty} \frac{d\omega}{2\pi} \left[ \tilde{C}_v(\omega) - 2k_B T \mathrm{Re}\,\tilde{\mu}(\omega) \right]$$

其中 $\tilde{C}_v(\omega)$ 是速度功率谱，$\tilde{\mu}(\omega)$ 是迁移率（响应函数的频域形式）。若系统处于平衡态，FDT 成立，括号内为零；若 FDT 违反，积分给出正的耗散率。

## 自由 OU 过程的特殊性

本论文的模型是**无位置势**的欠阻尼 OU 过程：

$$I\ddot\theta = -\gamma\dot\theta + M + \xi(t)$$

速度分量满足：

$$I\dot{v} = -\gamma v + M + \xi(t)$$

这是一个线性随机微分方程。其速度功率谱可以解析求解：

$$\tilde{C}_v(\omega) = \frac{2\gamma k_B T}{(I\omega)^2 + \gamma^2}$$

**关键观察**：上式与平衡态（$M=0$）的洛伦兹谱**完全一致**，与驱动力矩 $M$ 无关！

## 数值验证与物理解释

<figure style="text-align:center;margin:1.5em 0;">
  <img src="/images/research/HS_power_spectrum.png" alt="Power spectrum" style="max-width:480px;width:100%;border:1px solid #ddd;border-radius:4px;">
  <figcaption style="font-size:0.85em;color:#666;">不同驱动力矩 M 下的速度功率谱（散点）与平衡态洛伦兹谱（实线）完全重合</figcaption>
</figure>

**结论：**
- 谱方法（HS 关系）给出的耗散率 ≈ 0（FDT 在速度涨落上对任意驱动均成立）
- 熵产生方法给出的耗散率 ∝ $M^2$（非平衡耗散确实存在）

这一矛盾如何解释？

**物理图像**：驱动力矩 $M$ 产生的是**均值漂移**（有序角速度 $\langle v \rangle = M/\gamma$），而**涨落部分**（速度减去均值后的随机成分）完全不受 $M$ 影响。FDT 只刻画涨落，因此对任意 $M$ 均成立。耗散来自均值漂移，而非涨落–响应的失配。

这构成了一个"**平凡 NESS**"：系统处于非平衡稳态，但速度涨落的 FDT 仍然完全成立。HS 关系在此处给出零耗散，是因为 HS 方法探测的是涨落层面的 FDT 违反，而非均值流引起的耗散。

## 意义

这一结果揭示了 HS 关系的适用边界：对于**有位置势**（如周期棘轮势 $V(\theta)$）的系统，驱动会真正破坏涨落层面的 FDT，HS 方法才能给出非零的非平凡耗散。这也是后续引入可编程磁场势阱的重要动机之一。
