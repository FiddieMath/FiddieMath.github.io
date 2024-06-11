---
layout: default
title: 第8周：期中复习
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 8
nav_exclude: true
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

# 第8周作业

第8周没有作业

# 飞迪大学《数值分析》期中练习

考试范围：浮点数、函数插值、函数逼近．

{: .warning}
> 下面的练习与期中考试无关．部分题目来源已经给出

一、不定项选择题（20分）只有全选才能得5分，漏选或错选得0分．

1．以下关于 Lagrange 插值多项式的说法正确的是

A．Lagrange 插值多项式的导数通常易于计算

B．求 Lagrange 插值多项式不需要解线性方程组

C．用 $n+1$ 个基点得到的 Lagrange 插值多项式的次数恰为 $n$ 次

D．用 Lagrange 插值多项式 $p(x)$ 对一个已知函数 $f(x)$ 进行插值，增加插值点个数，可以使得 $\Vert p(x)-f(x)\Vert_{\infty}$ 下降．

&nbsp;

2．对 $n$ 维向量作快速 Fourier 变换，计算复杂度是

A．$O(\log n)$

B．$O(n\log n)$

C．$O(n^2)$

D．$O(n^2\log n)$
 
&nbsp;

3．下列函数中，不适合用来作为神经网络的激活函数的是

A．$f(x)=-\min\lbrace 2,x\rbrace$

B．$f(x)=0.9x+1$

C．$f(x)=\dfrac{1}{1+\mathrm{e}^{-x}}$ 

D．$f(x)=\left\lbrace\begin{aligned}
&\max\lbrace x,0.1x\rbrace, && x\ge 0, \\
&\min\lbrace x,0.1x\rbrace, && x < 0.
\end{aligned}\right.$

（来源：[2020年秋季Stanford-CS230-1/4考试](https://cs230.stanford.edu/files/cs230exam_fall20_soln.pdf) ）

&nbsp;

4．设 $T_n(x)$ 是 Chebyshev 多项式，$x_j = \cos\dfrac{(2j+1)\pi}{2(n+1)}$，$j=0,1,\cdots,n$．则 

A．当 $\vert x\vert \le 1$ 时，$\vert T_n(x)\vert \le 1$

B．对 $n=1,2,\cdots$，$T_{n+1}(x)=2xT_n(x)+T_{n-1}(x)$

C．$\lbrace T_n(x)\rbrace_{n=0}^{\infty}$ 是关于权函数 $\dfrac{1}{\sqrt{1-x^2}}$ 的正交多项式

D．对任意函数 $f(x)$，用 $\lbrace x_j\rbrace_{j=0}^n$ 作为基点得到的插值多项式比用其它基点得到的插值多项式的插值误差都要小



二、填空题（每题5分，共20分）

5．在计算机中计算函数 $f(x)=\sin x-\tan x$，当 $x\approx 0$ 时，为了避免相减相消，应把 $f(x)$ 改写为 ____________．

6．设 $f(x)=x^6+2x^4+3$，则 $f[2^0,2^1]=$ ___________， $f[2^0,2^1,2^2,\cdots,2^6]=$ ___________．

7．设 $x_0 < x_1 < \cdots < x_n$，$\ell_i(x)=\prod\limits_{j\ne i}\dfrac{x-x_j}{x_i-x_j}$，$i=0,1,\cdots,n$．则 $\sum\limits_{i=0}^n \ell_i(x) =$ ____________．

8．函数 $f(x)=x^2$，$x\in[0,1]$ 在 $\mathrm{span}\lbrace 1,x\rbrace$ 中的最佳一致逼近多项式是 $p(x)=$ ____________．

三、解答题（60分）

9．（12分）      
在双精度浮点数系中，设 $\alpha$ 是浮点数， $0 < \alpha < 10^{-8}$．证明：$\mathrm{fl}(\sin\alpha)=\alpha$．

（提示：双精度浮点数系的机器精度是 $2^{-52}$，$\lg 2\approx 0.3$）

（来源：[UC Berkeley Math128A](https://math.berkeley.edu/~mgu/MA128A/syllabus.html) ） 

&nbsp;

10．（12分）      
已知函数 $f(x)$ 在区间 $[0,2]$ 的三次样条函数为

$$p(x)=\left\lbrace\begin{aligned}
&3+x-9x^2, &&x\in[0,1],\\
&a+b(x-1)+c(x-1)^2+d(x-1)^3, &&x\in[1,2],
\end{aligned}\right.$$

（1）求 $a,b,c$ 的值；

（2）求 $d$ 使得 $\displaystyle\int_0^2[p^{\prime\prime}(x)]^2\mathrm{d}x$ 最小.

&nbsp;

11．（12分）     
考虑用函数 

$$f(x)=a\cos x+b\sin x+c\cos 2x$$

进行数据拟合：

|$x$   | $0$ | $\pi/2$ | $\pi$ | $3\pi /2$ |
|:----:|:---:|:---:|:---:|:---:|
|$y$ | $1$ | $1$ | $1$ | $0$ |

求 $a,b,c$ 使得 $\sum\limits_{i=1}^4 \vert f(x_i) - y_i \vert^2$ 最小．

（来源：2001年秋季UCLA博资考）

&nbsp;

12．（12分）     
设 $x_1\ne 0$，$f(x)$ 是三次连续可微的实值函数，证明存在唯一的四次多项式 $q(x)$ 使得 

$$\left\lbrace\begin{aligned}
&q^{(k)}(0)=f^{(k)}(0), \qquad k=0,1,2,3, \\
&q(x_1)=f(x_1).
\end{aligned}\right.$$

（来源：2020年春季UCLA博资考）

&nbsp;

13．（12分）     
考虑函数 $f(x)=\sin(kx)$，$x\in[0,2\pi]$ 的分段线性插值函数 $L(x)$，其中 $k\in\mathbb{Z}$．
插值基点为 $N+1$ 个点 $x_j=\dfrac{j}{N}$，$j=0,1,\cdots,N$．

估计使得 $\max\limits_{x\in[0,2\pi]}\vert f(x)-L(x)\vert < 0.01$成立的 $N$ 的下界（与 $k$ 有关）．

（来源：2013年秋季UCLA博资考）

&nbsp;

四、附加题（10分）

14．（5分）     
证明：对任何次数不超过 $n-1$ 次的多项式 $q(x)$ 与插值基点 $x_0 < x_1 < \cdots < x_n$，有

$$\sum\limits_{i=0}^nq(x_i)\prod\limits_{\substack{j=0 \\ j\ne i}}^n(x_i-x_j)^{-1}=0.$$

&nbsp;

15．(5分)     
设 $\boldsymbol{x}=(x_0,x_1,\cdots,x_{n-1})\in\mathbb{R}^n$，$\hat{\boldsymbol{x}}=(\hat{x}_0,\hat{x}_1,\cdots,\hat{x}_{n-1})$ 是它的离散Fourier变换，即

$$\hat{x}_j=\dfrac{1}{\sqrt{n}}\sum\limits_{k=0}^{n-1}x_k\mathrm{exp}(-2\pi\mathrm{i}jk/n), \quad j=0,1,\cdots,n-1.$$

证明：$\|\boldsymbol{x}\|_0\|\hat{\boldsymbol{x}}\|_0\ge n$，其中 $\|\boldsymbol{x}\|_0$ 表示 $\boldsymbol{x}$ 的非零分量个数．（提示：证明 $\hat{\boldsymbol{x}}$ 不可能有 $\|\boldsymbol{x}\|_0$ 个连续的零分量）

