---
layout: default
title: 第17周作业（理论14） 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 14
---

{: .no_toc }

<details open markdown="block">
  <summary>
    目录
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

# 第 17 周作业（理论14）

第五章 38(2)(4)、39

## 第 38(2) 题

{: .problem}
> 判断解初值问题
>
> $$y'=f(t,y), y(t_0)=y_0$$
>
> 的多步法 
>
> $$y_{n+2}+y_{n+1}-2y_n=h(2f_{n+1}+f_n)$$
>
> 是否收敛，为什么?

判断多步法收敛，只需判断相容且稳定．

（1）相容条件：

$$\begin{aligned}
&\rho(\lambda)=\lambda^2+\lambda-2, \\
&\rho'(\lambda)=2\lambda+1, \\
&\sigma(\lambda)=2\lambda+1.
\end{aligned}$$

因为 $\rho(1)=0$，$\rho'(1)=\sigma(1)=1$，所以这个多步法是相容的．

（2）稳定性条件：即判断特征根条件．$\rho(\lambda)$ 的两根为 $1$ 和 $-2$，有一根 $-2$ 不在单位圆内，故不是稳定的．

结合（1）（2），这个多步法不是收敛的．



## 第 38(4) 题

{: .problem}
> 判断解初值问题
>
> $$y'=f(t,y), y(t_0)=y_0$$
>
> 的多步法 
>
> $$y_{n+1}-y_{n-1}=\frac{h}{3}(3f_{n}-f_{n-1}+4f_{n-2})$$
>
> 是否收敛，为什么?


判断多步法收敛，只需判断相容且稳定．

（1）相容条件：

$$\begin{aligned}
&\rho(\lambda)=\lambda^3-\lambda, \\
&\rho'(\lambda)=3\lambda^2-1, \\
&\sigma(\lambda)=\dfrac{1}{3}(3\lambda^2-\lambda+4).
\end{aligned}$$

因为 $\rho(1)=0$，$\rho'(1)=\sigma(1)=2$，所以这个多步法是相容的．

（2）稳定性条件：即判断特征根条件．$\rho(\lambda)$ 的根为 $0,1,-1$，均在闭单位圆盘内，且 $1,-1$ 是单根．因此多步法是稳定的（注意：不是强稳定的，只是弱稳定的，因为 $\lambda=-1$ 不在单位圆内）．

结合（1）（2），这个多步法是收敛的．



## 第 39 题

{: .problem}
> 证明 Hamming 方法的校正公式是强稳定的.

 Hamming 方法的校正公式是

$$y_{n+1}=\dfrac{1}{8}[9y_n-y_{n-2}+3h(f_{n+1}+2f_n-f_{n-1})].$$

改写为

$$y_{n+1}-\dfrac{9}{8}y_n+\dfrac{1}{8}y_{n-2}=\dfrac{3}{8}h(f_{n+1}+2f_n-f_{n-1}),$$

因为

$$\begin{aligned}
\rho(\lambda)&=\lambda^3-\dfrac{9}{8}\lambda^2+\dfrac{1}{8} \\
&=\dfrac{1}{8}(\lambda-1)(8\lambda^2-\lambda-1),
\end{aligned}$$

则 $\rho(\lambda)$ 的所有根是 $1$，$\dfrac{1\pm\sqrt{33}}{16}$．除了 $1$ 之外，另外两个根均在单位圆内，故强根条件满足，从而这个格式是强稳定的．






