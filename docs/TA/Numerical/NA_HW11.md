---
layout: default
title: 第11周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 11
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

# 第11周作业

教材习题5：29、30、38、39、41、48

# 解答

## 第29题

{: .problem}
> 证明：计算积分 $\displaystyle I(f)=\int_a^bf(x)\mathrm{d}x$ 的 $n+1$ 个基点的求积公式
>
> $$I_n(f)=\sum\limits_{i=1}^{n+1}A_if(x_i)$$
>
> 的代数精确度至少是 $n$ 的充分必要条件是：
>
> $$A_i=\int_a^bl_i(x)\mathrm{d}x, \qquad i=1,\cdots,n+1.$$
>
> 其中
>
> $$l_i(x)=\prod\limits_{\substack{j=1 \\ j\ne i}}^{n+1}\dfrac{x-x_j}{x_i-x_j}.$$

**证明：** (1) 必要性：首先，$f(x)$ 的 Lagrange 插值多项式为 

$$p(x)=\sum\limits_{i=1}^{n+1}f(x_i)l_i(x).$$

由插值多项式误差公式，

$$f(x)-p(x)=\dfrac{1}{(n+1)!}f^{(n+1)}(\xi_x)w(x),$$

其中 $w(x)=\prod\limits_{i=1}^{n+1}(x-x_i)$．

对上式两边关于 $x\in(a,b)$ 积分，得

$$I(f)-\sum\limits_{i=1}^{n+1}f(x_i)\int_a^bl_i(x)\mathrm{d}x + \int_a^b\dfrac{1}{(n+1)!}f^{(n+1)}(\xi_x)w(x)\mathrm{d}x.$$

取 $f(x)=1,x,\cdots,x^n$，可知对 $k=0,1,\cdots,n$，有

$$I(x^k)=\sum\limits_{i=1}^{n+1} (x_i)^k\int_a^bl_i(x)\mathrm{d}x.$$

因为 $I_n(f)$ 的代数精确度至少为 $n$，所以

$$I(x^k)=I_n(x^k)=\sum\limits_{i=1}^{n+1} A_i\cdot(x_i)^k.$$

于是，

$$\sum\limits_{i=1}^{n+1} \left(A_i-\int_a^bl_i(x)\mathrm{d}x\right)\cdot (x_i)^k = 0, \qquad k=0,1,\cdots,n.$$

记矩阵

$$A=\begin{pmatrix}
1 & 1 & \cdots & 1 \\
x_1 & x_2 & \cdots & x_{n+1} \\
\vdots &\vdots & & \vdots \\
x_1^n & x_2^n & \cdots & (x_{n+1})^n
\end{pmatrix}\in\mathbb{M}^{n+1}(\mathbf{R})$$

并记列向量 $u=\left(A_i-\int_a^bl_i(x)\mathrm{d}x\right)_{i=1,\cdots,n+1}$．则

$$Au=0,$$

而 $A$ 是 Vandermonde 矩阵，它是非奇异的（其行列式不为 0），所以上述方程组只有零解，从而

$$A_i=\int_a^bl_i(x)\mathrm{d}x, \qquad i=1,2,\cdots,n+1.$$

(2) 充分性：假设 

$$A_i=\int_a^bl_i(x)\mathrm{d}x, \qquad i=1,2,\cdots,n+1.$$

$f(x)$ 的 Lagrange 插值多项式为 

$$p(x)=\sum\limits_{i=1}^{n+1}f(x_i)l_i(x),$$

两边积分，得

$$\int_a^bp(x)\mathrm{d}x=\sum\limits_{i=1}^{n+1}A_if(x_i).$$

则当 $f(x)=1,x,\cdots,x^n$ 时，由插值多项式误差公式得 $f(x)=p(x)$，故

$$\int_a^bf(x)\mathrm{d}x=\int_a^bp(x)\mathrm{d}x=\sum\limits_{i=1}^{n+1}A_if(x_i).$$

所以 $I_n(f)$ 的代数精度至少是 $n$．

## 第30题

{: .problem}
> 用代数精确度较高的求积公式来计算积分是否必得到较精确的结果？研究例子
>
> $$I=\int_{-1}^1(-8+45x^2-25x^4)\mathrm{d}x,$$
>
> 取步长 $h=1$，应用 Simpson 公式和复合梯形公式进行计算．


## 第38题

{: .problem}
> 试确定 $A_{-1},A_0,A_1$，使求积公式
>
> $$\int_{-1}^1f(x)\mathrm{d}x\approx A_{-1}f(-1)+A_0f(0)+A_1f(1)$$
>
> 对 $f(x)=1,\mathrm{e}^x,\mathrm{e}^{2x},\mathrm{e}^{3x}$ 都准确成立．

令 $f(x)=1$，$\mathrm{e}^x$，$\mathrm{e}^{2x}$，得

$$\begin{aligned}
2&=A_{-1}+A_0+A_1, \\
\mathrm{e}-\mathrm{e}^{-1} &=A_{-1}\mathrm{e}^{-1}+A_0+A_1\mathrm{e}, \\
\dfrac{1}{2}\mathrm{e}^2-\dfrac{1}{2}\mathrm{e}^{-2}&=A_{-1}\mathrm{e}^{-2} + A_0 + A_1\mathrm{e}^2.
\end{aligned}$$

解得

$$\begin{aligned}
A_{-1}&=\dfrac{-\mathrm{e}^2+2\mathrm{e}+2+2\mathrm{e}^{-1}-\mathrm{e}^{-2}}{2(\mathrm{e}-1-\mathrm{e}^{-1}+\mathrm{e}^{-2})},\\
A_0&=\dfrac{\mathrm{e}^2+\mathrm{e}-4-4\mathrm{e}^{-1}-\mathrm{e}^{-2}-\mathrm{e}^{-3}}{2(\mathrm{e}-1-\mathrm{e}^{-1}+\mathrm{e}^{-2})}, \\
A_1&=\dfrac{\mathrm{e}-2-2\mathrm{e}^{-1}+6\mathrm{e}^{-2}+\mathrm{e}^{-3} }{2(\mathrm{e}-1-\mathrm{e}^{-1}+\mathrm{e}^{-2})}, \\
\end{aligned}$$

经检验，上述 $A_{-1},A_0,A_1$ 也满足

$$\dfrac{1}{3}(\mathrm{e}^3-\mathrm{e}^{-3})=A_{-1}\mathrm{e}^{-3}+A_0+A_1\mathrm{e}^3.$$

## 第39题

{: .problem}
> 设 $P_n(x)$ 和 $T_n(x)$ 分别表示 $n$ 次 Legendre 多项式和 Chebyshev 多项式，证明
>
> (1) $\vert P_{2n}(\sqrt{x})\vert$ 是 $[0,1]$ 上关于权函数 $\dfrac{1}{\sqrt{x}}$ 的直交多项式序列；
>
> (2) $\left\vert \dfrac{1}{\sqrt{x}} P_{2n+1}(\sqrt{x})\right\vert$ 是 $[0,1]$ 上关于权函数 $\sqrt{x}$ 的直交多项式序列；
>
> (3) $\left\vert \dfrac{1}{\sqrt{x}} T_{2n+1}(\sqrt{x})\right\vert$ 是 $[0,1]$ 上关于权函数 $\left(\dfrac{x}{1-x}\right)^{\frac{1}{2}}$ 的直交多项式序列．

提示：验证直交多项式的定义即可，需要用到 Legendre 多项式和 Chebyshev 多项式的直交性质．对于一个多项式序列 $\lbrace f_n\rbrace$，它在 $[0,1]$ 关于权函数 $W(x)$ 是直交多项式序列，等价于当 $m\ne n$ 时，

$$\int_0^1f_m(x)f_n(x)W(x)\mathrm{d}x.$$



## 第41题

{: .problem}
> 求 Gauss 求积公式
>
> $$\int_0^1f(x)\ln x\mathrm{d}x\approx A_1f(x_1)+A_2f(x_2)$$
>
> 的系数 $A_1$, $A_2$ 以及基点 $x_1$, $x_2$，并导出离散误差．

解答：从这个视频的 13:48 开始看：

[https://www.bilibili.com/video/BV1vF411T7kY/](https://www.bilibili.com/video/BV1vF411T7kY/)

## 第48题

{: .problem}
> 作适当变换，应用 Gauss-Chebyshev 求积公式计算积分
>
> $$I=\int_1^3 x\sqrt{4x-x^2-3}\mathrm{d}x$$

令 $t=x-2$，$4x-x^2-3=(x-1)(3-x)$．则

$$\begin{aligned}
I&=\int_{-1}^1 (t+2)\sqrt{1-t^2}\mathrm{d}t \\
&=\int_{-1}^1 \dfrac{(t+2)(1-t^2)}{\sqrt{1-t^2}}\mathrm{d}t \\
\end{aligned}$$

设 $f(t)=(t+2)(1-t^2)$，它是 3 次多项式，只需用 2 点 Gauss-Chebyshev 求积公式是

$$\begin{aligned}
\int_{-1}^1f(x)(1-x^2)^{-\frac{1}{2}}\mathrm{d}x
&=\dfrac{\pi}{2}\left(f(\cos\dfrac{\pi}{4})+f(\cos\dfrac{3\pi}{4})\right) \\
&= \pi.
\end{aligned}$$

## 第49题

{: .problem}
> 作一个适当变换，把积分
>
> $$I=\int_0^{\frac{1}{3}}\dfrac{6x}{\sqrt{x(1-3x)}}\mathrm{d}x$$
>
> 化为能应用 $n$ 点 Gauss-Chebyshev 求积公式的积分．当 $n$ 为何值时，能得积分的准确值？并用 Gauss-Chebyshev 求积公式计算它的准确值．

需要把区间 $[0,\dfrac{1}{3}]$ 变成 $[-1,1]$，作变换 $t=6(x-\dfrac{1}{6})=6x-1$ 即可．这样 $t\in[-1,1]$，

$$\begin{aligned}
I&=\int_{-1}^1\dfrac{1}{6}\cdot \dfrac{t+1}{\sqrt{\frac{t+1}{6}(1-\frac{3(t+1)}{6})}} \mathrm{d}t \\
&=\int_{-1}^1\dfrac{t+1}{\sqrt{3(1-t^2)}} \mathrm{d}t. \\
\end{aligned}$$

设 $f(x)=\dfrac{x+1}{\sqrt{3}}$，它是一次多项式，只需用一点 Gauss-Chebyshev 求积公式是

$$\begin{aligned}
\int_{-1}^1f(x)(1-x^2)^{-\frac{1}{2}}\mathrm{d}x
&= \pi f(0)  \\
&= \dfrac{\pi}{\sqrt{3}}.
\end{aligned}$$

也可用两点 Gauss-Chebyshev 求积公式

$$\begin{aligned}
\int_{-1}^1f(x)(1-x^2)^{-\frac{1}{2}}\mathrm{d}x
&=\dfrac{\pi}{2}\left(f(\cos\dfrac{\pi}{4})+f(\cos\dfrac{3\pi}{4})\right) \\
&= \dfrac{\pi}{\sqrt{3}}.
\end{aligned}$$





