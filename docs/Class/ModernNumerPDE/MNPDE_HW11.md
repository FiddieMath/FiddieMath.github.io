---
layout: default
title: 第11周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 11
---

# 第11周作业

提交截止日期：2024 年 11 月 24 日 23:55:59

## HW15 

{: .problem}
> （讲义第六章作业题2）
>
> 证明 引理6.11：存在常数 $\alpha_0>0$，当 $\mathrm{Re}\,\gamma\ge-\alpha_0, \vert\gamma\vert\lesssim 1$ 时,
> $$
> \Vert w-P_h^{\pm}w\Vert_{L^2(\Omega)}+h\Vert w-P_h^{\pm}w\Vert_{H^1(\Omega)}+h^{\frac{1}{2}}\Vert w-P_h^{\pm}w\Vert_{L^2(\Gamma)}\lesssim h^2\vert w\vert_{H^2(\Omega)}.
> $$
> （提示：先估计 $\Vert P_h^{\pm}w-I_hw\Vert_{H^1(\Omega)}$）

证明要用到改进的对偶论证、有限元逆估计、迹定理．

注意，对于前两项，要分别估计 $P_h^+$ 和 $P_h^-$ 的情形，与 2021 年上课时的记号不一样．

