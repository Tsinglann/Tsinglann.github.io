---
permalink: /research/
title: "Research / 研究工作"
author_profile: true
---

本页面展示我在毕业论文中开展的主要数值模拟工作与结果。所有仿真均基于欠阻尼朗之万方程（Euler–Maruyama 离散格式），在 MATLAB 中实现。

*This page presents the main numerical simulation work and results from my undergraduate thesis. All simulations are based on the underdamped Langevin equation (Euler–Maruyama scheme), implemented in MATLAB.*

---

## 1. 热力学不确定性关系 | Thermodynamic Uncertainty Relation (TUR)

**背景 / Background**

热力学不确定性关系（TUR）给出了非平衡稳态中"精度"（流的信噪比）与"能耗"（熵产生）之间的下界约束：

$$\mathcal{Q} = \frac{\mathrm{Var}(J)}{\langle J \rangle^2} \cdot \frac{\langle \dot{\Sigma} \rangle}{2} \geq 1$$

*The TUR sets a lower bound on the tradeoff between precision (signal-to-noise of a current) and dissipation (entropy production) in nonequilibrium steady states.*

**结果 / Results**

在欠阻尼系统中，惯性效应导致在有限时间窗口内 $\mathcal{Q} \approx 0.80 < 1$，
而过阻尼系统精确饱和到 $\mathcal{Q} \approx 1.00$。这一差异与驱动力矩无关，纯为惯性修正。

*In the underdamped system, inertia leads to* $\mathcal{Q} \approx 0.80 < 1$ *within finite time windows,
while the overdamped system saturates the bound* $\mathcal{Q} \approx 1.00$. *This discrepancy is independent of driving torque — a pure inertial effect.*

<div style="display: flex; gap: 1em; flex-wrap: wrap; justify-content: center; margin: 1.5em 0;">
  <div style="text-align: center;">
    <img src="/images/research/TUR_result.png" alt="TUR Result" style="max-width: 380px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">TUR 参数 Q 随时间窗口的演化 / Q vs. observation time window</p>
  </div>
  <div style="text-align: center;">
    <img src="/images/research/TUR_comparison.png" alt="TUR Comparison" style="max-width: 380px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">欠阻尼与过阻尼系统对比 / Underdamped vs. overdamped comparison</p>
  </div>
</div>

---

## 2. 线性响应有效范围 | Valid Range of Linear Response

**背景 / Background**

涨落–耗散定理（FDT）将平衡态响应函数与平衡态关联函数联系起来。在非平衡稳态驱动下，
FDT 重建的响应 $\chi_\mathrm{FDT}(t)$ 与直接阶跃响应 $\chi_\mathrm{direct}(t)$ 是否一致？
线性近似在何种扰动幅值 $h_0$ 下仍然有效？

*The FDT links equilibrium response functions to equilibrium correlation functions.
In a nonequilibrium steady state, does the FDT-reconstructed response agree with the direct step response?
For what perturbation amplitude* $h_0$ *does the linear approximation hold?*

**结果 / Results**

三者（直接响应、FDT 重建、解析理论）吻合良好；相对偏差 $|\delta\chi|$ 随 $h_0$ 单调降低，
$h_0 \gtrsim 0.5$ 后低于 5%。偏差来源为有限系综信噪比，非物理非线性。

*All three methods agree well; the relative deviation* $|\delta\chi|$ *decreases monotonically with* $h_0$,
*falling below 5% for* $h_0 \gtrsim 0.5$. *The deviation originates from finite-ensemble noise, not physical nonlinearity.*

<div style="display: flex; gap: 1em; flex-wrap: wrap; justify-content: center; margin: 1.5em 0;">
  <div style="text-align: center;">
    <img src="/images/research/LR_range_chi_t.png" alt="Linear Response chi(t)" style="max-width: 380px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">响应函数 χ(t) 比较 / Response function χ(t) comparison</p>
  </div>
  <div style="text-align: center;">
    <img src="/images/research/LR_range_result.png" alt="Linear Response Range" style="max-width: 380px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">线性响应有效范围扫描 / Linear response validity scan</p>
  </div>
</div>

---

## 3. Harada–Sasa 谱耗散关系 | Harada–Sasa Spectral Dissipation Identity

**背景 / Background**

Harada–Sasa（HS）关系通过速度功率谱与 FDT 违反量来估计系统的能量耗散率。
对于无位置势的自由 OU 过程（本文模型），非平衡稳态中速度的 FDT 是否仍然成立？

*The Harada–Sasa identity estimates the energy dissipation rate from the violation of FDT in velocity power spectra.
For a free Ornstein–Uhlenbeck process (this model) driven out of equilibrium,
does FDT still hold for velocity fluctuations?*

**结果 / Results**

自由 OU 过程的速度功率谱在任意驱动下与平衡态洛伦兹谱一致——构成"平凡 NESS"：
谱方法给出耗散率 ≈ 0，而熵产生方法给出耗散率 ∝ $M^2$。
这揭示：耗散来自均值漂移（有序转动），而非涨落–响应的失配。

*The velocity power spectrum of a free OU process matches the equilibrium Lorentzian at any driving — a "trivial NESS":
the spectral method yields dissipation ≈ 0, while the entropy-production method gives dissipation ∝* $M^2$.
*This reveals that dissipation originates from the mean drift (ordered rotation), not from fluctuation-response mismatch.*

<div style="display: flex; gap: 1em; flex-wrap: wrap; justify-content: center; margin: 1.5em 0;">
  <div style="text-align: center;">
    <img src="/images/research/HS_power_spectrum.png" alt="HS Power Spectrum" style="max-width: 380px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">速度功率谱（不同驱动力矩）/ Velocity power spectrum at different driving torques</p>
  </div>
  <div style="text-align: center;">
    <img src="/images/research/HS_result.png" alt="HS Result" style="max-width: 380px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">HS 耗散估计与熵产生对比 / HS dissipation estimate vs. entropy production</p>
  </div>
</div>

---

## 4. 布朗卡诺热机 | Brownian Carnot Heat Engine

**背景 / Background**

基于可编程磁场控制方案，我们设计了一种颗粒布朗卡诺热机循环：通过等温压缩/膨胀与
绝热等效温度切换实现卡诺循环。分析了惯性效应对效率和功率的影响。

*Based on the programmable magnetic control scheme, we designed a granular Brownian Carnot engine cycle:
isothermal compression/expansion combined with adiabatic effective-temperature switching.
Inertial effects on efficiency and power are analyzed.*

<div style="display: flex; gap: 1em; flex-wrap: wrap; justify-content: center; margin: 1.5em 0;">
  <div style="text-align: center;">
    <img src="/images/research/mode1_shape_5__A_1_5_k_BT.png" alt="BCE Mode 1" style="max-width: 300px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">势阱形状模拟（模式 1）/ Potential well shape (mode 1)</p>
  </div>
  <div style="text-align: center;">
    <img src="/images/research/mode2_shape5.png" alt="BCE Mode 2" style="max-width: 300px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">非对称棘轮势 / Asymmetric ratchet potential</p>
  </div>
  <div style="text-align: center;">
    <img src="/images/research/mode3_multi_shape.png" alt="BCE Mode 3" style="max-width: 300px; width: 100%; border: 1px solid #ddd; border-radius: 4px;">
    <p style="font-size: 0.85em; color: #666;">多种势场叠加 / Multiple potential shapes</p>
  </div>
</div>

---

## 系统框架 | System Framework

整个研究从同一欠阻尼随机系统出发，覆盖从**被动统计观测**到**主动最优控制**的完整路径：

*The entire study starts from the same underdamped stochastic system, covering the complete path from passive statistical observation to active optimal control:*

```
欠阻尼朗之万方程 / Underdamped Langevin Equation
        ↓
   数值模拟验证 / Numerical Verification
  ┌────────────────────────────────────────┐
  │  涨落定理  │  TUR  │  FDT & LR  │  HS  │
  └────────────────────────────────────────┘
        ↓
   实验对应 / Experimental Correspondence
  (颗粒布朗马达 / Granular Brownian Motor)
        ↓
   主动调控 / Active Control
  (磁场可编程势阱 / Programmable Magnetic Potential)
        ↓
   热力学应用 / Thermodynamic Applications
  ┌──────────────────────────────────────────────────┐
  │ 最优输运 │ Landauer 擦除 │ 布朗卡诺热机          │
  │ Optimal transport │ Information erasure │ Carnot │
  └──────────────────────────────────────────────────┘
```

---

*代码实现 / Code: MATLAB (Euler–Maruyama scheme, ensemble averaging)*
*论文答辩 / Defense: April 2026, Lanzhou University*
