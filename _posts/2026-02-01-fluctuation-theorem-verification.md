---
title: '涨落定理的数值验证'
date: 2026-02-01
permalink: /posts/2026/02/fluctuation-theorem-verification/
tags:
  - fluctuation theorem
  - entropy production
  - numerical simulation
  - 涨落定理
  - 熵产生
---

## 两种熵产生定义

在随机热力学框架中，对欠阻尼布朗转子存在两种等价的熵产生定义：

**热力学熵产生**（路径无关定义）：

$$\Delta S^{(I)} = \frac{Q_\text{env}}{T} = \frac{\gamma \int_0^\tau (\dot{\theta} - \langle\dot\theta\rangle)^2\, dt}{T}$$

**轨迹熵产生**（路径积分定义），通过正向轨道概率与时间反演轨道概率之比定义：

$$\Delta S^{(II)} = \ln \frac{P[\theta(t)]}{P[\tilde\theta(t)]}$$

理论上两者应满足同样的涨落定理。

## 涨落定理的检验

涨落定理的对称函数形式：

$$\mathrm{Sym}(\sigma) \equiv \ln \frac{P(\Delta S = +\sigma)}{P(\Delta S = -\sigma)} = \sigma$$

即以 $\sigma$ 为横坐标作图，斜率应为 1。

## 数值结果

对欠阻尼布朗转子（参数 $I, \gamma, T, M$ 由实验数据反推），采用 Euler–Maruyama 格式数值积分，生成 $10^4$ 条独立轨道，统计熵产生分布。

**主要结论：**
- $\Delta S^{(I)}$ 与 $\Delta S^{(II)}$ 的概率分布形状高度一致
- 对称函数 $\mathrm{Sym}(\sigma)$ 与理论直线（斜率为 1）符合良好
- 两种定义在主要区间内均支持涨落定理，定性验证成功

实验数据也在主要区间内分布于理论直线附近，给出定性支持（大涨落区统计稀少，弥散性较大，属正常有限样本效应）。

## 数值参数

| 参数 | 含义 | 取值 |
|------|------|------|
| $I$ | 转动惯量 | 由自相关拟合反推 |
| $\gamma$ | 阻尼系数 | 由自相关拟合反推 |
| $T_\text{eff}$ | 有效温度 | 由速度方差反推 |
| $M$ | 驱动力矩 | 扫描多个值 |
| $\Delta t$ | 时间步长 | $10^{-3}\ \tau$ |
| $N_\text{traj}$ | 轨道数 | $10^4$ |
