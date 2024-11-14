---
layout: default
title: 第10周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 10
---

# 第10周作业

提交截止日期：2024 年 11 月 17 日 23:55:59

## HW14 

{: .problem}
> （讲义第六章作业题3）
>
> 假设 $\Omega$ 是边界充分光滑的严格星形区域，推导问题
> $$
> \begin{aligned}
> &-\Delta u-k^2u=0, &x\in\Omega, \label{HW1701} \\
> &\dfrac{\partial u}{\partial\boldsymbol{n}}+\mathbf{i} ku=g, &x\in\Gamma,\label{HW1702}
> \end{aligned}
> $$
> 的二次有限元离散的$H^1$误差估计．
>
> 其中，$\Gamma=\partial\Omega,\mathbf{i}=\sqrt{-1}$ 是虚数单位，$\boldsymbol{n}$ 是 $\partial\Omega$ 的单位外法向量，$f\in H^1(\Omega)$，$g\in H^{\frac{3}{2}}(\Gamma)$．

**注：** 因为涉及到二次有限元离散，这里我添加了条件 $f\in H^1(\Omega)$，$g\in H^{\frac{3}{2}}(\Gamma)$．

