---
layout: default
title: 第8周作业
parent: 偏微分方程现代数值方法
grand_parent: 上课笔记
nav_order: 8
---



# 第8周作业

提交截止日期：2024 年 11 月 3 日 23:55:59

## HW10 

{: .problem}
> （讲义第四章作业题8）
>
> 证明引理5.2的Gauss-Seidel情形：
>
> 设 $P_k^i$ 为到 $\{\phi_k^i\}$ 张成的空间的投影：
>
> $$a(P_k^iw_k,\phi_k^i)=a(w_k,\phi_k^i), \qquad \forall w_k\in V_k,$$
>
> 则Gauss-Seidel迭代法的等价算子形式的迭代子满足
>
> $$R_kg=(I-E_k)A_k^{-1}g,$$
>
> 其中$E_k=(I-P_k^{a_k})\cdots(I-P_k^1).$



## HW11

{: .problem}

> 将有限元方程 $A_ku_k=f_k$ 的多重网格 $V$ 循环算法改写为如下形式：
>
> 取 $u^0\in V_k$，做迭代
>
> $$u^{n+1}=MG(u^n,A_k,f_k), \quad n=0,1,2,\cdots.$$

多重网格法的 $\mathbb{B}_k$ 是递归定义的，只需把 $\mathbb{B}_k$ 都改为 $MG(\cdot,A_k,\cdot)$．
