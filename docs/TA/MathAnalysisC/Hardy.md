---
layout: default
title: 补充内容：Hardy不等式的变种
parent: 数学分析C
grand_parent: 助教工作
nav_order: 101
---

{: .problem}
> 设$u:\mathbb{R}^6\to\mathbb{R}$是具有紧支集的光滑函数, 证明
> 
> $$\left(\int_{\mathbb{R}^6}\vert \nabla u\vert ^2\mathrm{d}x\right)^{\frac{1}{2}}
> \left(\int_{\mathbb{R}^6}u^2\mathrm{d}x\right)^{\frac{1}{2}}
> \ge 2.5\int_{\mathbb{R}^6}\dfrac{u^2}{\vert x\vert }\mathrm{d}x.$$

**证明：** 本题要证

$$\left(\int_{\mathbb{R}^6}\vert \nabla u\vert ^2\mathrm{d}x\right)^{\frac{1}{2}}
\left(\int_{\mathbb{R}^6}u^2\mathrm{d}x\right)^{\frac{1}{2}}
\le \dfrac{5}{2}\int_{\mathbb{R}^6}\dfrac{u^2}{\vert x\vert }\mathrm{d}x.$$

我们为方便起见, 记维数$d=6$. 由于$u$具有紧支集, 因此存在$r>0$使得$\mathrm{supp}(u)\subset B_r=\lbrace x:\vert x\vert \le r\rbrace$,
于是$u$在$B_r$的边界与外部都等于$0$, 即$u\vert _{\partial B_r}=0$.

本题需要用到**分部积分公式**: 设$f,g:\Omega\to\mathbb{R}$充分光滑, 其中$\Omega\subset\mathbb{R}^d$, 则

$$\int_{\Omega}fg_{x_i}\mathrm{d}x=-\int_{\Omega}gf_{x_i}\mathrm{d}x+\int_{\partial\Omega}fgn_i\mathrm{d}S,
\qquad i=1,\cdots,d,$$

其中, $\boldsymbol{n}=(n_1,\cdots,n_d)$是边界$\partial \Omega$上的单位外法向量.

我们定义$g(x)=\dfrac{1}{\vert x\vert }$. 首先我们注意到, $\nabla g = \nabla\left(\dfrac{1}{\vert x\vert }\right)=-\dfrac{x}{\vert x\vert ^3}$.
这是因为,

$$g_{x_i}=\dfrac{\partial}{\partial x_i}\left(\dfrac{1}{(x_1^2+\cdots+x_d^2)^{\frac{1}{2}}}\right)
=\dfrac{-x_i}{(x_1^2+\cdots+x_d^2)^{\frac{3}{2}}}.$$

于是,

$$\int_{\mathbb{R}^d}\dfrac{u^2}{\vert x\vert }\mathrm{d}x
=\int_{B_r}u^2\dfrac{x\cdot x}{\vert x\vert ^3}\mathrm{d}x
=-\int_{B_r}u^2x\cdot \nabla\left(\dfrac{1}{\vert x\vert }\right)\mathrm{d}x.$$

很自然的, 我们可以定义$f^{(k)}=u^2x_k$, 即$f^{(k)}(x)=u^2(x)x_k$, 其中$k=1,2,\cdots,d$. 于是

$$\begin{aligned}
\text{上式}&=-\int_{\mathbb{R}^d}\sum\limits_{i=1}^d f^{(i)}g_{x_i}\mathrm{d}x \\
&=\int_{B_r}\sum\limits_{i=1}^d f^{(i)}_{x_i}g\mathrm{d}x -
\int_{\partial B_r}\sum\limits_{i=1}^df^{(i)}g n_i\mathrm{d}S
&&\text{(分部积分公式)} \\
\end{aligned}$$

计算可得$f^{(i)} _ {x_i}=2uu_{x_i}x_i + u^2$. 注意$f^{(i)}=u^2x_i$在边界$B_r$上等于$0$, 因此上式第二项的曲面积分等于$0$, 于是

$$\begin{aligned}
\int_{\mathbb{R}^d}\dfrac{u^2}{\vert x\vert }\mathrm{d}x&=\int_{B_r}g\sum\limits_{i=1}^d (2uu_{x_i}x_i+u^2)\mathrm{d}x\\
&=\int_{B_r}\dfrac{1}{\vert x\vert } 2u\nabla u\cdot x + d\dfrac{u^2}{\vert x\vert }\mathrm{d}x\\
\end{aligned}$$

整理可得

$$(1-d)\int_{\mathbb{R}^d}\dfrac{u^2}{\vert x\vert }\mathrm{d}x=2\int_{B_r}\dfrac{1}{\vert x\vert } u\nabla u\cdot x.$$

接下来用一下Cauchy-Schwarz不等式:

$$\begin{aligned}
\vert 1-d\vert \int_{\mathbb{R}^d}\dfrac{u^2}{\vert x\vert }\mathrm{d}x
&\le 2\int_{B_r}\dfrac{1}{\vert x\vert } \vert u\vert \vert \nabla u\vert \cdot \vert x\vert \mathrm{d}x \\
& = 2\int_{B_r} \vert u\vert \vert \nabla u\vert \mathrm{d}x \\
&\le 2\left(\int_{B_r}\vert u\vert ^2\mathrm{d}x\right)^{\frac{1}{2}}\left(\int_{B_r}\vert \nabla u\vert ^2\mathrm{d}x\right)^{\frac{1}{2}}
\end{aligned}$$

把$d=6$代进去即可完成证明.$\square$

{: .remark}
> **注：** 原来的问题的不等号右边是没有平方的, 即问题形如
> 
> {: .problem}
> > 设$u:\mathbb{R}^6\to\mathbb{R}$是具有紧支集的光滑函数, 证明
> > 
> > $$\left(\int_{\mathbb{R}^6}\vert \nabla u\vert ^2\mathrm{d}x\right)^{\frac{1}{2}}
> > \left(\int_{\mathbb{R}^6}u^2\mathrm{d}x\right)^{\frac{1}{2}}
> > \ge 2.5\left(\int_{\mathbb{R}^6}\dfrac{u^2}{\vert x\vert }\mathrm{d}x\right)^{\frac{1}{2}}.$$
> 
> 
> 考虑$r>0$, 利用$u(x)=\vert x\vert \chi_{B_r}$验证即可, 其中$\chi$是示性函数.
> 则$\nabla u = \dfrac{x}{\vert x\vert }\chi_{B_r}$, 注意六维球的体积是$\dfrac{1}{6}\pi^3r^6$,
> 于是可算得$\int_{B_r}\vert x\vert ^k\mathrm{d}x = \dfrac{\pi^3}{6}\cdot\dfrac{r^{k+6}}{k+7}$, 并且
> 
> $$\big\| \vert \nabla u\vert \big\| _2\cdot\| u\| _2 = \dfrac{\pi^3}{18}r^7 > \dfrac{5\pi^3}{96}r^7=2.5\big\| \vert x\vert ^{-\frac{1}{2}}u\big\| _2^2. $$
> 
> ($r$的次数相同并且$\dfrac{1}{18} > \dfrac{5}{96}$, 故不等式成立. )
> 如果没有平方, 那么右边就变成$r^{3.5}$的常数倍, 左右两边$r$的次数不相同, 当$r$充分小时右边更大.
> 
> 你可能会说这个$u(x)$不是光滑函数啊! 没关系, 反正本题不等式的$u$都位于积分里面, 只要各阶弱导数存在即可.
