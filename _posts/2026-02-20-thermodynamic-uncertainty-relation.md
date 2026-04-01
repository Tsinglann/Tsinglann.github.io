---
title: '热力学不确定性关系：欠阻尼惯性效应'
date: 2026-02-20
permalink: /posts/2026/02/thermodynamic-uncertainty-relation/
tags:
  - TUR
  - thermodynamic uncertainty relation
  - underdamped
  - inertia
  - 热力学不确定性关系
  - 欠阻尼
---

## 热力学不确定性关系

热力学不确定性关系（TUR）是近年来非平衡统计物理的重要进展，给出非平衡稳态中"精度"与"能耗"之间的普适下界：

$$\mathcal{Q} \equiv \frac{\mathrm{Var}(J)}{\langle J \rangle^2} \cdot \frac{\langle \dot{\Sigma} \rangle \tau}{2} \geq 1$$

其中 $J$ 是时间积分流（如角位移），$\langle \dot{\Sigma} \rangle$ 是熵产生率，$\tau$ 是观测时间窗口。

TUR 的物理含义：要减小流的相对涨落（提高精度），就必须增大熵产生（提高能耗）。这一关系最初在**过阻尼**系统中得到严格证明。

## 欠阻尼的惯性修正

对于**欠阻尼**系统，惯性项的存在使系统在短时间内具有"记忆效应"，角速度不能瞬间调整。直觉上，惯性使粒子在短时间内保持当前运动状态，减小了相对涨落，从而使 $\mathcal{Q}$ 可能低于 1。

## 数值结果

分别对欠阻尼和过阻尼两种系统进行模拟：

| 系统 | $\mathcal{Q}$（短时） | $\mathcal{Q}$（长时） |
|------|----------|----------|
| 欠阻尼 | **≈ 0.80** | 趋近 1 |
| 过阻尼 | ≈ 1.00 | 精确饱和 |

**关键发现：**
- 欠阻尼系统在有限时间窗口内 $\mathcal{Q} \approx 0.80 < 1$，违反了过阻尼 TUR 下界
- 随观测时间增长，$\mathcal{Q}$ 逐渐趋近 1（惯性效应在长时间尺度消失）
- 这一差异与驱动力矩 $M$ 的大小无关，是**纯粹的惯性效应**

<figure style="text-align:center;margin:1.5em 0;">
  <img src="/images/research/TUR_comparison.png" alt="TUR comparison" style="max-width:480px;width:100%;border:1px solid #ddd;border-radius:4px;">
  <figcaption style="font-size:0.85em;color:#666;">欠阻尼（蓝）与过阻尼（红）系统的 TUR 参数 Q 随观测时间的演化</figcaption>
</figure>

## 物理解释

惯性项 $I\ddot\theta$ 使粒子在短时间内"沿惯性"运动，等效于减小了噪声驱动的随机偏离，因此流的相对涨落 $\mathrm{Var}(J)/\langle J\rangle^2$ 短暂减小，$\mathcal{Q}$ 低于 1。这一效应在时间 $\sim I/\gamma$（动量弛豫时间）后消失，长时行为回归过阻尼极限。
