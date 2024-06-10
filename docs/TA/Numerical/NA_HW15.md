---
layout: default
title: 第15周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 15
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

# 第15周作业

教材习题10：36、38(3)

# 解答

## 第36题

{: .problem}
> 设正实数列 $u_0,u_1,u_2,\cdots$ 满足递推不等式
>
> $$u_{n+1}\le u_n+\sum\limits_{j=0}^ma_ju_{n-j}+b,$$
>
> 其中 $n=m,m+1,m+2,\cdots$，而 $a_j\ge 0$，$j=0,1,\cdots,m$，$b\ge 0$．试证明：对 $n=0,1,2,\cdots$，有
>
> $$u_n\le \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{nA}-\dfrac{b}{A},$$
>
> 其中实数 $\delta \ge u_j$，$j=0,1,\cdots,m$，并且，$A=\sum\limits_{j=0}^ma_j\ne 0$．

**注：** 这个不等式叫做 **离散Gronwall不等式**．

**证明：** 首先这个不等式对 $n=0,1,\cdots,m$ 显然成立．下面用第二数学归纳法来证明对 $n\ge m$ 也成立．

假设 $u_n\le \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{nA}-\dfrac{b}{A}$ 当 $n\le k$ 时成立（$k\ge m$），则对 $n=k+1$，

$$\begin{aligned}
u_{k+1}&\le u_k+\sum\limits_{j=0}^ma_ju_{k-j}+b \\
&\le \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{kA}-\dfrac{b}{A} + \sum\limits_{j=0}^ma_j\left[\left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{(k-j)A}-\dfrac{b}{A}\right]+b \\
&=\left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{kA} + \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{kA}\sum\limits_{j=0}^ma_j\mathrm{e}^{-jA} -\dfrac{b}{A} \\
&\le \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{kA} + \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{kA} A\sum\limits_{j=0}^m\mathrm{e}^{-jA} -\dfrac{b}{A} \\
&\le \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{kA}(1+A)-\dfrac{b}{A} \\
&\le \left(\delta+\dfrac{b}{A}\right)\mathrm{e}^{(k+1)A}-\dfrac{b}{A}.
\end{aligned}$$

证明完成．


## 第38(3)题

{: .problem}
> 判断解初值问题
>
> $$y'=f(t,y), y(t_0)=y_0$$
>
> 的多步法 
>
> $$y_n-y_{n-1}=\dfrac{h}{12}(5f_n+8f_{n-1}-f_{n-2})$$
>
> 是否收敛，为什么?

判断多步法收敛，只需判断相容且稳定．

（1）相容条件：

$$\begin{aligned}
&\rho(\lambda)=\lambda^2-\lambda, \\
&\rho'(\lambda)=2\lambda-1, \\
&\sigma(\lambda)=\dfrac{1}{12}(5\lambda^2+8\lambda-1).
\end{aligned}$$

因为 $\rho(1)=0$，$\rho'(1)=\sigma(1)=1$，所以这个多步法是相容的．

（2）稳定性条件：即判断根条件．$\rho(\lambda)$ 的两根为 $0$ 和 $1$，它都在单位圆中，并且单位圆周上的根 $1$ 是单根．
因此多步法是稳定的．

结合（1）（2），这个多步法是收敛的．






