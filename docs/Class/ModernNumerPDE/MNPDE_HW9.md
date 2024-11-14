---
layout: default
title: 第9周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 9
---

# 第9周随堂练习

{: .problem}
> **随堂练习 qz7（判断题）：** 求解二阶椭圆问题线性有限元方法的多重网格 V 循环算法的计算量是最优阶的．

**答：** 错误．多重网格 V 循环算法的计算量是 $O(n\log n)$，“完全多重网格方法(FMG)” 的计算量是 $O(n)$．

我看漏了“完全”二字，把这题弄错了．

# 第9周作业

提交截止日期：2024 年 11 月 11 日 23:55:59

## HW12 

{: .problem}
> （讲义第五章作业题3）
>
> 利用完全多重网格方法求解如下椭圆问题的线性有限元离散：
>
> ​    $$\begin{aligned}
>​    -\nabla\cdot(a\nabla u)&=1, \qquad x\in\Omega:=(-1,1)\times(-1,1), \\
> ​    u&=0, \qquad x\in\partial\Omega,
>​    \end{aligned}\qquad a=\left\lbrace\begin{aligned}
> ​    &1, &&x_1x_2>0, \\
>​    &10, &&x_1x_2\le 0.
> ​    \end{aligned}\right.$$
>
> 探究不同的$l$的选取对多重网格法所求近似解的精度的影响(参见定理5.8, 与直接法的解或与$V$循环多重网格解比较即可).

## HW13

{: .problem}

> （讲义第六章作业题1）
>
> 设 $\Omega=\Omega_1\setminus\Omega_0\subset\mathbb{R}^d(d=2,3)$，其中 $\Omega_0\subset\Omega_1$ 都是多面体且关于某一点 $x_0\in\Omega_0$ 都是严格的星型区域．考虑Helmholtz方程：
> $$
> \begin{aligned}
>  -\Delta u-k^2u&=f, \qquad x\in\Omega, \\
>   \dfrac{\partial u}{\partial \boldsymbol{n}}+iku&=g, \qquad x\in\partial\Omega_1, \\
> u&=0,  \qquad x\in\partial\Omega_0. 
> \end{aligned}
> $$
> 推导其稳定性估计．



