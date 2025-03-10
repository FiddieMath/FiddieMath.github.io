---
layout: default
title: 第3周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 3
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


# 第3周作业（理论3）

讲义第二章习题3、6、7

# 解答

## 第3题

{: .problem}
> 用 81, 100, 121 的平方根求 $\sqrt{95}$．

考虑对数据 $(81,9)$，$(100,10)$，$(121,11)$ 用 Lagrange 插值，得到

$$p(x)=9\dfrac{(x-100)(x-121)}{(81-100)(81-121)}+10\dfrac{(x-81)(x-121)}{(100-81)(100-121)}+11\dfrac{(x-81)(x-100)}{(121-81)(121-100)}.$$

则 $\sqrt{95}\approx p(95) = \dfrac{1111}{114} = 9.74561\cdots$．

注：真实值为 $\sqrt{95}=9.74679\cdots$．

**【错解】** 用数据 $(9,81)$，$(10,100)$，$(11,121)$ 进行 Lagrange 插值，肯定会得到 $f(x)=x^2$．本题应找出 $f^{-1}(x)=\sqrt{x}$ 的 Lagrange 插值函数．本题也体现了 Lagrange 插值在求反函数在某些点处的近似值上的应用．

## 第6题

{: .problem}
> 设$x_0,x_1,\cdots,x_n$为$n+1$个相异的插值基点，$l_i(x)(i=0,1,\cdots,n)$为Lagrange基本多项式，证明
>
> (1) $\sum\limits_{i=0}^nl_i(x)=1$；
>
> (2) $\sum\limits_{i=0}^nx_i^jl_i(x)=x^j$，$j=1,2,\cdots,n$；
>
> (3) $\sum\limits_{i=0}^n(x_i-x)^jl_i(x)=0$，$j=1,2,\cdots,n$；
>
> (4) 
>
> $$\sum\limits_{i=0}^nl_i(0)x_i^j=\left\{\begin{aligned}
&1, &&j=0, \\
&0, &&j=1,2,\cdots,n, \\
&(-1)^nx_0x_1\cdots x_n, &&j=n+1.
\end{aligned}\right.$$

(1)和(2)分别考虑对$f(x)=1$和$f(x)=x^j$，$j=1,2,\cdots,n$用Lagrange插值公式，得到$n$次多项式$p_n(x)$．因为此时$f$的$n+1$次导数是0，根据插值误差公式，有

$$|f(x)-p_n(x)|\equiv 0.$$

所以$f(x)\equiv p_n(x)$．

(3)用二项式展开

$$(x_i-x)^j=x_i^j-\mathrm{C}_j^1x_i^{j-1}x+\cdots+(-1)^j\mathrm{C}_j^jx^j$$

和

$$(1-1)^j=1-\mathrm{C}_j^1+\cdots+(-1)^j\mathrm{C}_j^j=0.$$

(4)只看$j=n+1$的情形（$j=0,1,\cdots,n$均可由前三问推出）．

让$f(x)=x^{n+1}$，得到$n$次Lagrange插值多项式，此时$f^{(n+1)}(x)=(n+1)!$，根据带余项的Lagrange插值公式，有

$$f(x)-p_n(x) = \dfrac{f^{(n+1)}(\xi)}{(n+1)!}w_{n+1}(x)
= w_{n+1}(x).$$

其中，

$$p_n(x)=\sum\limits_{i=0}^nf(x_i)l_i(x)=\sum\limits_{i=0}^nx_i^nl_i(x).$$

让$x=0$即可．

## 第7题

{: .problem}
> 假定要造计算零阶 Bessel 函数
>
> $$I_0(x)=\dfrac{1}{\pi}\int_0^{\pi}\cos(x\sin t)\mathrm{d}t$$
>
> 的等距数值表，问如何选取表距 $h$，使利用这个数值表作线性插值时, 误差不超过 $10^{-6}$？

解答：首先

$$\begin{aligned}
I_0'(x)&=\dfrac{1}{\pi}\int_0^{\pi}-\sin(x\sin t)\sin t\mathrm{d}t, \\
I_0^{\prime\prime}(x)&=\dfrac{1}{\pi}\int_0^{\pi}-\cos(x\sin t)\sin^2 t\mathrm{d}t, \\
&=-\dfrac{1}{\pi}\cos(x\sin\eta)\int_0^{\pi}\sin^2t\mathrm{d}t=-\dfrac{1}{2}\cos(x\sin\eta),
\end{aligned}$$

其中 $\eta\in(0,\pi)$．

在区间 $[x_0,x_0+h]$ 采用线性插值时，由 Lagrange 插值的余项公式，存在 $\xi\in[x_0,x_0+h]$ 使得

$$r_1(x)=\dfrac{I_0^{\prime\prime}(\xi)}{2!}w_{2}(x)=-\dfrac{1}{4}\cos(\xi\sin\eta)w_2(x), $$

当 $x\in[x_0,x_0+h]$ 时，$\vert w_2(x)\vert = \vert(x-x_0)[x-(x_0+h)]\vert \le \dfrac{h^2}{4}$．所以

$$\vert r_1(x)\vert \le \dfrac{h^2}{16}.$$

令 $\dfrac{h^2}{16} \le 10^{-6}$，得 $h\le 4\times 10^{-3}$．

因此选取表距不超过 $4\times 10^{-3}$ 时，可以让误差不超过 $10^{-6}$．只要给出的 $h$ 符合估计，均可作为答案，比如有同学写 $1\times 10^{-3}$ 也是可以的．

**【错解】** 本题有同学没理解好题意，对 $I_0(x)$ 指定了一个插值区间 （比如 $[0,1]$ ）然后用 $n+1$ 个点进行 Lagrange 插值．

应当知道：数值表将函数的输入与输出值以表格形式呈现，用户可以快速查找特定点的函数值，而无需每次都进行计算．

比如同学们如果《概率论基础》这门课学到正态分布一节，会接触到“标准正态分布表”（概率论教材书后附录）．设 $X\sim N(0,1)$，分布函数是 $\Phi(x)=P(X\le x)$，那么给出的就是表距为 $10^{-3}$ 时标准正态分布函数的值．如果需要计算其它值，比如 $\Phi(1.962)$，那么最简便的方法肯定是用  $\Phi(1.96)$ 和 $\Phi(1.97)$ 的真实值得到线性插值函数 $p(x)$ ，然后用 $p(1.962)$ 作为 $\Phi(1.962)$ 的近似值，而不会去用多个点计算高次 Lagrange 插值．

如果特殊数值表精度不符合要求，一般不会采用高次 Lagrange 插值来提升精度（因为可能会有 Runge 现象），而是会对数值表进行加密，取更小的 $h$ 得到更精密的数据．

虽然本题的 Bessel 函数的可以估计出 $\vert I_0^{(n)}(x)\vert \le 1$，不会有 Runge 现象，但这只是碰巧这个例子能够使用 $n$ 次多项式插值来提升精度；换个例子就不一定有类似的高阶导数上界了．







