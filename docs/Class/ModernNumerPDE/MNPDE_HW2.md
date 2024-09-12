---
layout: default
title: 第2周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 2
---

# 第2周随堂练习

{: .problem}
> **随堂练习 qz1（判断题）：** 设 $\Omega$ 是二维空间中边界是 Lipschitz 的有界区域，则 $H^1(\Omega)$ 连续嵌入到 $L^{\infty}(\Omega)$．

**答：** 否．

设 Banach 空间 $X,Y$ 满足 $X\subset Y$．$X$ 连续嵌入到 $Y$，指的是 $\Vert u\Vert_Y\le C\Vert u\Vert_X$ 对任意 $u\in X$ 都成立．

考虑 $\Omega=\lbrace x\in\mathbb{R}^2:\vert x\vert < 1/2\rbrace$．
考虑函数 $f(x)=\ln\vert \ln\vert x\vert\vert$，则 $f\in H^1(\Omega)$，但 $f\notin L^{\infty}(\Omega)$．

但是，可以证明：如果 $1\le q < \infty$，$\Omega\subset\mathbb{R}^2$，则 $H^1(\Omega)$ 连续嵌入到 $L^q(\Omega)$．


# 第2周作业

提交截止日期：2024 年 9 月 ？ 日 23:55:59

## HW3 

还没布置