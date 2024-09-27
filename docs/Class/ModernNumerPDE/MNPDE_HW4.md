---
layout: default
title: 第4周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 4
---

# 第4周随堂练习

{: .problem}
> **随堂练习 qz3（判断题）：** 有限元的形函数必须取为多项式函数．

**答：** 否．形函数 (shape function) 可以是各种各样的，只要可以写成一组线性无关的函数的线性组合．比如：多尺度基函数．

# 第4周作业

提交截止日期：2024 年 10 月 8 日 23:55:59

## HW5 

{: .problem}
> 设 $\Omega$ 是带 Lipschitz 边界的有界区域，$a(x),c(x)\in L^{\infty}(\Omega)$，$a(x)\ge a_0 > 0$，$c(x)\ge 0$，$f\in H^{-1}(\Omega)$． 
>
> 变分问题：求 $u\in H^1(\Omega)$，$u\vert _ {\partial\Omega}=g$，使得
>
> $$
> a(u,v)=\langle f,v\rangle \qquad \forall v\in H_0^1(\Omega) \tag{4.1}
> $$
>
> 其中双线性形式 $a$ 如下定义：
>
> $$
> a(u,v)=\int_{\Omega}(a\nabla u\cdot\nabla v+cuv)\mathrm{d}x. \tag{4.2}
> $$
> 
> 取有限维子空间 $V_h\subset H^1(\Omega)$，$g_h\in V_h\vert _ {\partial\Omega}$ 为 $g$ 的近似，则相应的 Galerkin 离散为：求 $u_h\in V_h$，$u_h \vert _ {\partial\Omega}=g_h$ 使得
>
> $$
> a(u_h,v_h)=\langle f,v_h\rangle \qquad \forall v_h\in V_h\cap H_0^1(\Omega) \tag{4.3}
> $$
> 
> 证明 **引理3.9** ：设 $u$ 和 $u_h$ 分别是变分问题 $(4.1)$ 及其 Galerkin 离散 $(4.2)$ 的解．则成立如下误差估计：
>
> $$
> \Vert u-u_h\Vert _ {H^1(\Omega)}\le\left(1+\dfrac{\beta}{\alpha}\right)\inf\limits_{\substack{v _ h\in V _ h \\ v _ h\vert _ {\partial\Omega}=g_h}}\Vert u-v _ h\Vert _ {H^1(\Omega)}. \tag{4.4}
> $$
> 
