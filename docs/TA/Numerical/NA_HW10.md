---
layout: default
title: 第12周作业（理论10） 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 10
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

# 第 12 周作业（理论10）

第四章 34、35、37、38

# 解答

### 第34题解答

{: .problem}
> 给出计算积分
>
> $$\int_{-1}^1f(x)(1+x^2)\mathrm{d}x$$
>
> 的两点插值求积公式，使它的代数精度为 3，并导出求积公式的离散误差．

（1）求积公式的推导．

**【方法一】** 设 

$$I_2(f)=c_1f(x_1)+c_2f(x_2),$$

因为代数精度为 3，所以令 $f(x)=1,x,x^2,x^3$，那么求积公式精确成立，得方程组

$$\left\lbrace
\begin{aligned}
&\dfrac{8}{3}=c_1+c_2, && \text{①}\\
&0=c_1x_1+c_2x_2, && \text{②}\\
&\dfrac{16}{15}=c_1x_1^2+c_2x_2^2, && \text{③} \\
&0=c_1x_1^3+c_2x_2^3.&& \text{④}
\end{aligned}
\right.$$

由②④得 $x_1=-x_2$，

再代入①②得 $c_1=c_2=\dfrac{4}{3}$，

由③得 $x_1=-\dfrac{2\sqrt{5}}{5}$，$x_2=\dfrac{2\sqrt{5}}{5}$．

**【方法二】** 设 $p_n(x)$ 是按权函数 $w(x)=1+x^2$ 的正交多项式，$p_0(x)=1$，

按正交多项式的递推式，即 (3.3.3) 式（2025年版讲义），计算可得：

$p_1(x)=x$，$p_2(x)=x^2-\dfrac{2}{5}$．

由 Gauss 求积公式的性质，$x_1,x_2$ 是 $p_2(x)$ 的两根．

所以 $x_1=-\dfrac{2\sqrt{5}}{5}$，$x_2=\dfrac{2\sqrt{5}}{5}$．

在求 $c_1,c_2$ 时，因为当 $f(x)=x-x_1$ 和 $f(x)=x-x_2$ 时，求积公式精确成立，得关于 $c_1,c_2$ 的方程，从而得所求结果．


（2）离散误差的推导．

由(4.6.7)式，误差公式是

$$E_n(f)=\dfrac{f^{(4)}(\xi)}{4!}\int_{-1}^1(x^2-\dfrac{2}{5})^2(1+x^2)\mathrm{d}x=\dfrac{17}{1575}f^{(4)}(\xi).$$


## 第35题

{: .problem}
> 求 Gauss 求积公式
>
> $$\int_0^1f(x)\ln x\mathrm{d}x\approx A_1f(x_1)+A_2f(x_2)$$
>
> 的系数 $A_1$, $A_2$ 以及基点 $x_1$, $x_2$，并导出离散误差．

从这个视频的 13:48 开始看，必须**一键三连**．

[https://www.bilibili.com/video/BV1vF411T7kY/](https://www.bilibili.com/video/BV1vF411T7kY/)


## 第37题

{: .problem}
> 用三点 Gauss-Legendre 求积公式计算积分 $\displaystyle\int_0^1\dfrac{\sin x}{1+x}\mathrm{d}x$ 的近似值．

先换元：$t=2x-1$，则 $t\in[-1,1]$，积分换成

$$\int_{-1}^1\dfrac{\sin\frac{t+1}{2}}{t+3} \mathrm{d}t,$$

设 $f(t)=\dfrac{\sin\frac{t+1}{2}}{t+3}$，三点 Gauss-Legendre 求积公式：

$$I_3(f)=c_1f(x_1)+c_2f(x_2)+c_3f(x_3),$$

其中 $x_1,x_2,x_3$ 是方程 $L_3(x)=\dfrac{1}{2}(5x^3-3x)=0$ 的三个根，$c_1=c_3=\dfrac{5}{9}$，$c_2=\dfrac{8}{9}$．用这个求积公式就能得出近似值．



## 第38题

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














