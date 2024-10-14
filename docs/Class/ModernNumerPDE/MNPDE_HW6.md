---
layout: default
title: 第6周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 6
---

# 第6周随堂练习

{: .problem}
> **随堂练习 qz5（判断题）：** Deny-Lions 引理与 Bramble-Hilbert 引理等价．

**答：** 是．证明 Bramble-Hilbert 引理的中间步骤用到了 Deny-Lions 引理，反之， Deny-Lions 引理又是 Bramble-Hilbert 引理的一个特殊情形．

# 第6周作业

提交截止日期：2024 年 10 月 20 日 23:55:59

## HW7 

{: .problem}
> 
> 编程用线性有限元方法求解条形区域上的Poisson方程
>
> $$\left\lbrace\begin{aligned}
&-\Delta u=1, \quad x\in\mathbb{R}, \quad  y\in(0,1), \\
&u(x,0)=u(x,1)=0, \quad  u(x+1,y)=u(x,y).
\end{aligned}\right.$$
>
> 讨论有限元解误差的收敛阶，提交数值试验报告． 
> 
> 提示：只要在一个周期上比如单位正方形 $\Omega=(0,1)\times(0,1)$ 上求解；初始网格用 ```initmesh``` 的话要检查网格在$x$方向的周期性，用 ```poimesh``` 可以生成标准等腰直角三角形剖分；精确解可以写出来；误差可以考虑 $L^2$ 或 $L^{\infty}$ 误差．

编程的难点在于如何把周期边界条件体现在系数矩阵中．

## HW8

{: .problem}
> 
> 设单元 $K$ 与 $\hat{K}\subset\mathbb{R}^d$ 仿射等价，证明局部的 Poincare 不等式：
>
> $$\Vert v-v_K\Vert_{L^2(K)}\le Ch_K\Vert\nabla v\Vert_{L^2(K)}, \forall v\in H^1(K).$$
>
> 其中 $\displaystyle v_K=\dfrac{1}{|K|}\int_Kv$，$C=C(\hat{K})$．

没什么难度，关键是把积分区域变到参考单元中．
