---
layout: default
title: 第7周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 7
---

# 第7周随堂练习

{: .problem}
> **随堂练习 qz6（判断题）：** 用经典的 Gauss-Seidel 迭代法求解有限元方程组的计算量是最优阶的．

**答：** 从逻辑上看，如果经典的 Gauss-Seidel 迭代法达到了最优阶，就不会有后面的多重网格法了．所以这个是错误的．

# 第7周作业

提交截止日期：2024 年 10 月 27 日 23:55:59

## HW9 

{: .problem}
> 
> （讲义第四章作业题8）
> 对非齐次Dirichlet椭圆边值问题：设 $\Omega$ 是多边形（多面体）区域，$a(x),c(x)\in L^{\infty}(\Omega)$，$a(x)\ge a_0>0$，$c(x)\ge 0$，$f\in H^{-1}(\Omega)$，变分问题为：求 $u\in H^1(\Omega)$，$u|_{\partial\Omega}=g$ 使得
> 
> $$a(u,v)=\langle f,v\rangle, \qquad \forall v\in H_0^1(\Omega)$$
> 
> 其中双线性形式如下定义
> 
> $$a(u,v)=\int_{\Omega}(a\nabla u\cdot\nabla v+cuv)\mathrm{d}x.$$
> 
> 给出线性有限元离散，并推导 $H^1$ 和 $L^2$ 误差估计．

本题仿照书上的零边界条件情形的过程来写即可，但是这里边界条件非零，需要作一定的修改，关键是要取 $g_h\in V_h$ 为 $g$ 在 $V_h$ 上的投影．


