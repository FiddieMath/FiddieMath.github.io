---
layout: default
title: 第5周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 5
---

# 第5周随堂练习

{: .problem}
> **随堂练习 qz4（判断题）：** 三角剖分上的 Lagrange 二次有限元空间是 $H^1(\Omega)$ 的子空间，从而是 $H^1$-协调的．

**答：** 是．因为 Lagrange 二次有限元的解是 $C^0$ 的，根据定理 3.18，解也位于 $H^1$ 空间中，所以是 $H^1$-协调的．

# 第5周作业

提交截止日期：2024 年 10 月 8 日 23:55:59

## HW6 

{: .problem}
> 
> 证明 Argyris 有限元空间 $\widetilde{V}_h\subset C^1(\Omega)$，从而 $\widetilde{V}_h\subset H^2(\Omega)$．

提示：仿照讲义的例 3.17．关键是证明相邻两个单元的公共边上的函数值与梯度值都是连续的，只需证明相邻两个单元上的函数在这条公共边上的函数值与梯度值之差都为 $0$ 即可．