---
layout: default
title: 第3周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 3
---

# 第3周随堂练习

{: .problem}
> **随堂练习 qz2（判断题）：** 对二阶椭圆问题，Robin 边界条件是自然边界条件．

**答：** 是．Neumann 边界条件和 Robin 边界条件都是自然边界条件．

# 第3周作业

提交截止日期：2024 年 9 月 29 日 23:55:59

## HW4 

设 $\Omega=\lbrace x:0 < x_i < T_i, 1\le i\le d\rbrace$，$f\in L^2(\Omega)$，考虑周期边界条件的 Poisson 问题的变分形式：求 $u\in H_{\mathrm{per}}^1(\Omega)$ 满足

$$\text{(VP)}\qquad \int_{\Omega}\nabla u\cdot\nabla v\mathrm{d}x=\int_{\Omega}fv\mathrm{d}x, \qquad \forall v\in H_{\mathrm{per}}^1(\Omega),$$

证明 (VP) 存在弱解的充要条件是 $\int_{\Omega}f\mathrm{d}x=0$．


