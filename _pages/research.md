---
permalink: /research/
title: ""
author_profile: true
---

<div class="lang-zh">
<h1>研究工作</h1>
<p>本页面展示毕业论文中的主要数值模拟工作与结果。所有仿真均基于欠阻尼朗之万方程（Euler–Maruyama 离散格式），在 MATLAB 中实现。</p>
</div>

<div class="lang-en">
<h1>Research</h1>
<p>This page presents the main numerical simulation results from my undergraduate thesis. All simulations are based on the underdamped Langevin equation (Euler–Maruyama scheme), implemented in MATLAB.</p>
</div>

---

## 1. <span class="lang-zh">热力学不确定性关系</span><span class="lang-en">Thermodynamic Uncertainty Relation (TUR)</span>

<div class="lang-zh">
<p><strong>背景：</strong>热力学不确定性关系（TUR）给出非平衡稳态中"精度"（流的信噪比）与"能耗"（熵产生）之间的下界约束：</p>

$$\mathcal{Q} = \frac{\mathrm{Var}(J)}{\langle J \rangle^2} \cdot \frac{\langle \dot{\Sigma} \rangle}{2} \geq 1$$

<p><strong>结果：</strong>欠阻尼系统在有限时间窗口内 Q ≈ 0.80 &lt; 1，过阻尼系统精确饱和到 Q ≈ 1.00。差异与驱动力矩无关，纯为惯性修正。</p>
</div>

<div class="lang-en">
<p><strong>Background:</strong> The TUR sets a lower bound on the tradeoff between precision (signal-to-noise of a current) and dissipation (entropy production) in nonequilibrium steady states:</p>

$$\mathcal{Q} = \frac{\mathrm{Var}(J)}{\langle J \rangle^2} \cdot \frac{\langle \dot{\Sigma} \rangle}{2} \geq 1$$

<p><strong>Results:</strong> In the underdamped system, inertia leads to Q ≈ 0.80 &lt; 1 within finite time windows, while the overdamped system saturates the bound at Q ≈ 1.00. This discrepancy is independent of driving torque — a pure inertial effect.</p>
</div>

<div style="display:flex;gap:1em;flex-wrap:wrap;justify-content:center;margin:1.5em 0;">
  <div style="text-align:center;">
    <img src="/images/research/TUR_result.png" alt="TUR Result" style="max-width:380px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">TUR 参数 Q 随时间窗口的演化</span><span class="lang-en">Q vs. observation time window</span></p>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/TUR_comparison.png" alt="TUR Comparison" style="max-width:380px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">欠阻尼与过阻尼系统对比</span><span class="lang-en">Underdamped vs. overdamped comparison</span></p>
  </div>
</div>

---

## 2. <span class="lang-zh">线性响应有效范围</span><span class="lang-en">Valid Range of Linear Response</span>

<div class="lang-zh">
<p><strong>背景：</strong>FDT 重建响应 χ_FDT(t) 与直接阶跃响应 χ_direct(t) 的一致性，以及线性近似在何种扰动幅值 h₀ 下仍然有效。</p>
<p><strong>结果：</strong>三者（直接响应、FDT 重建、解析理论）吻合良好；相对偏差 |δχ| 随 h₀ 单调降低，h₀ ≳ 0.5 后低于 5%。偏差来源为有限系综信噪比，非物理非线性。</p>
</div>

<div class="lang-en">
<p><strong>Background:</strong> Whether the FDT-reconstructed response χ_FDT agrees with the direct step response χ_direct, and for what perturbation amplitude h₀ the linear approximation holds.</p>
<p><strong>Results:</strong> All three methods (direct response, FDT reconstruction, analytic theory) agree well; the relative deviation |δχ| decreases monotonically with h₀, falling below 5% for h₀ ≳ 0.5. The deviation originates from finite-ensemble noise, not physical nonlinearity.</p>
</div>

<div style="display:flex;gap:1em;flex-wrap:wrap;justify-content:center;margin:1.5em 0;">
  <div style="text-align:center;">
    <img src="/images/research/LR_range_chi_t.png" alt="Response function" style="max-width:380px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">响应函数 χ(t) 三种方法比较</span><span class="lang-en">Response function χ(t): three-method comparison</span></p>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/LR_range_result.png" alt="Linear Response Range" style="max-width:380px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">线性响应有效范围扫描</span><span class="lang-en">Linear response validity scan over h₀</span></p>
  </div>
</div>

---

## 3. <span class="lang-zh">Harada–Sasa 谱耗散关系</span><span class="lang-en">Harada–Sasa Spectral Dissipation Identity</span>

<div class="lang-zh">
<p><strong>背景：</strong>Harada–Sasa（HS）关系通过速度功率谱与 FDT 违反量估计能量耗散率。对于无位置势的自由 OU 过程，NESS 中速度 FDT 是否仍然成立？</p>
<p><strong>结果：</strong>自由 OU 过程的速度功率谱在任意驱动下与平衡态洛伦兹谱一致（"平凡 NESS"）——谱方法耗散率 ≈ 0，而熵产生方法耗散率 ∝ M²。耗散来自均值漂移（有序转动），非涨落–响应失配。</p>
</div>

<div class="lang-en">
<p><strong>Background:</strong> The Harada–Sasa identity estimates energy dissipation from the FDT violation in velocity power spectra. For a free OU process driven out of equilibrium, does FDT still hold for velocity fluctuations?</p>
<p><strong>Results:</strong> The velocity power spectrum matches the equilibrium Lorentzian at any driving — a "trivial NESS": spectral method gives dissipation ≈ 0, while the entropy-production method gives dissipation ∝ M². Dissipation originates from the mean drift (ordered rotation), not fluctuation-response mismatch.</p>
</div>

<div style="display:flex;gap:1em;flex-wrap:wrap;justify-content:center;margin:1.5em 0;">
  <div style="text-align:center;">
    <img src="/images/research/HS_power_spectrum.png" alt="HS Power Spectrum" style="max-width:380px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">速度功率谱（不同驱动力矩）</span><span class="lang-en">Velocity power spectrum at different driving torques</span></p>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/HS_result.png" alt="HS Result" style="max-width:380px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">HS 耗散估计与熵产生对比</span><span class="lang-en">HS dissipation estimate vs. entropy production</span></p>
  </div>
</div>

---

## 4. <span class="lang-zh">布朗卡诺热机</span><span class="lang-en">Brownian Carnot Heat Engine</span>

<div class="lang-zh">
<p><strong>背景：</strong>基于可编程磁场控制方案，设计颗粒布朗卡诺热机循环：通过等温压缩/膨胀与绝热等效温度切换实现卡诺循环，分析惯性效应对效率和功率的影响。</p>
</div>

<div class="lang-en">
<p><strong>Background:</strong> Based on the programmable magnetic control scheme, a granular Brownian Carnot engine is designed: isothermal compression/expansion combined with adiabatic effective-temperature switching. Inertial effects on efficiency and power are analyzed.</p>
</div>

<div style="display:flex;gap:1em;flex-wrap:wrap;justify-content:center;margin:1.5em 0;">
  <div style="text-align:center;">
    <img src="/images/research/mode1_shape_5__A_1_5_k_BT.png" alt="BCE Mode 1" style="max-width:300px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">势阱形状（模式 1）</span><span class="lang-en">Potential well shape (mode 1)</span></p>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/mode2_shape5.png" alt="BCE Mode 2" style="max-width:300px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">非对称棘轮势</span><span class="lang-en">Asymmetric ratchet potential</span></p>
  </div>
  <div style="text-align:center;">
    <img src="/images/research/mode3_multi_shape.png" alt="BCE Mode 3" style="max-width:300px;width:100%;border:1px solid #ddd;border-radius:4px;">
    <p style="font-size:0.85em;color:#666;"><span class="lang-zh">多种势场叠加</span><span class="lang-en">Multiple potential shapes</span></p>
  </div>
</div>

---

<div class="lang-zh">
<h2>系统框架</h2>
<p>整个研究从同一欠阻尼随机系统出发，覆盖从<strong>被动统计观测</strong>到<strong>主动最优控制</strong>的完整路径：</p>
</div>

<div class="lang-en">
<h2>System Framework</h2>
<p>The entire study starts from the same underdamped stochastic system, covering the complete path from <strong>passive statistical observation</strong> to <strong>active optimal control</strong>:</p>
</div>

```
Underdamped Langevin / 欠阻尼朗之万
            ↓
   Numerical Verification / 数值验证
 ┌──────────────────────────────────┐
 │  FT  │  TUR  │  FDT/LR  │  HS  │
 └──────────────────────────────────┘
            ↓
  Experiment / 实验（颗粒布朗马达）
            ↓
  Active Control / 主动调控（磁场势阱）
            ↓
  Applications / 热力学应用
 ┌────────────────────────────────────────┐
 │ Optimal Transport │ Erasure │ Carnot   │
 │ 最优输运          │ 信息擦除 │ 卡诺热机 │
 └────────────────────────────────────────┘
```
