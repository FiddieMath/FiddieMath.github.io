---
layout: default
title: 第4周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 4
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


# 第4周作业（理论4）

讲义第二章习题 12, 13, 15, 17, 19, 20

# 解答

## 第12题

{: .problem}
> 设 $f(x)$ 为 $x$ 的 $k$ 次多项式，$x_1,x_2,\cdots,x_m$ 为互不相同的实数，且 $k>m$，证明 $f[x,x_1,\cdots,x_m]$ 为 $x$ 的 $k-m$ 次多项式．

用下面Newton均差的迭代定义式进行归纳：

$$f[x,x_1,\cdots,x_n]=\dfrac{f[x_1,x_2,\cdots,x_n]-f[x,x_1,\cdots,x_{n-1}]}{x_n-x}.$$

## 第13题

{: .problem}
> 设 $a=x_0 < x_1 < x_2 < \cdots < x_{n-1} < x_n=b$，函数 $f(x)\in C^1[a,b]$，则差商
> 
> $$g(x):=f[x,x_0,x_1,\cdots,x_n]$$
> 
> 关于 $x$ 在 $[a,b]$ 上连续．这里 $g(x)$ 在节点 $x_k$ 上的值是通过重节点差商来定义的．进一步，若 $f(x)\in C^2[a,b]$，则有
> 
> $$g'(x)=f[x,x,x_0,x_1,\cdots,x_n],$$
> 
> 且 $g'(x)$ 也关于 $x$ 在 $[a,b]$ 上连续．

**这个问题解决的关键是在第一类间断点处进行补充定义．**

下面的引理 1 是习题二的第 6 题：

{: .highlight-title}
> Lemma
> 
> **引理 1：** $\sum\limits_{j=0}^n\prod\limits_{\substack{k=0 \\ k\ne j}}^n\dfrac{x-x_k}{x_j-x_k}=1$

**证明：** 考虑常值函数 $f(x)=1$ 的 Lagrange 插值多项式，应用代数基本定理或 Lagrange 插值多项式的余项公式即可得结论．

{: .highlight-title}
> Lemma
> 
> **引理 2：** 若 $x$, $x_0$, $x_1$, $\cdots$, $x_n$ 是 $n+2$ 个不同的点，则
>
> $$f[x_0,x_1,\cdots,x_n,x]=\sum\limits_{j=0}^n\dfrac{f[x,x_j]}{\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)}.$$

**证明：** 函数 $f(t)$ 在节点 $x_0$, $x_1$, $\cdots$, $x_n$ 的 Newton 插值多项式为

$$Q_n(t)=f[x_0]+(t-x_0)f[x_0,x_1]+\cdots+(t-x_0)\cdots(t-x_{n-1})f[x_0,x_1,\cdots,x_n].\tag{1}$$

再引入节点 $x$，则 $f(t)$ 在节点 $x_0$, $x_1$, $\cdots$, $x_n$, $x$ 的插值多项式为

$$Q_{n+1}(t)=Q_n(t)+q_{n+1}(t), \tag{2}$$

其中 $q_{n+1}(t)=a_{n+1}\prod\limits_{k=0}^n(t-x_k)$．

由 $Q_{n+1}(x)=f(x)$，(2)式可化为 

$$a_{n+1}=\dfrac{f(x)-Q_n(x)}{\prod\limits_{k=0}^n(x-x_k)}=\dfrac{f(x)-Q_n(x)}{w_{n+1}(x)},$$

其中 $w_{n+1}(x)=\prod\limits_{k=0}^n(x-x_k)$．

另一方面，函数 $f(t)$ 在节点 $x_0$, $x_1$, $\cdots$, $x_n$ 的 Lagrange 插值多项式为

$$Q_n(t)=\sum\limits_{j=0}^nf(x_j)\prod\limits_{\substack{k=0 \\ k\ne j}}^n\dfrac{t-x_k}{x_j-x_k} 
=\sum\limits_{j=0}^nf(x_j)\dfrac{w_{n+1}(t)}{(t-x_j)\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)} \tag{3}$$

根据 Newton 插值多项式的性质，$a_{n+1}=f[x_0,x_1,\cdots,x_n,x]$．

$$\begin{aligned}
f[x_0,x_1,\cdots,x_n,x]&=\dfrac{f(x)-Q_n(x)}{w_{n+1}(x)} \\
&=\dfrac{f(x)}{w_{n+1}(x)}-\sum\limits_{j=0}^nf(x_j)\dfrac{1}{(x-x_j)\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)} 
\end{aligned} \tag{4}$$

由引理 1， $\sum\limits_{j=0}^n\dfrac{1}{(x-x_j)\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)}=w_{n+1}(x)$  ，把它代入(4)式可得

$$\begin{aligned}
f[x_0,x_1,\cdots,x_n,x]
&=\sum\limits_{j=0}^n\dfrac{f(x)-f(x_j)}{(x-x_j)\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)} \\
&=\sum\limits_{j=0}^n\dfrac{f[x,x_j]}{\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)}.
\end{aligned}$$

证明完毕． $\square$

{: .theorem}
> **定理3：** 
>
> 若 $f\in C[a,b]$，$x_j\in[a,b]$，$f'(x_j)$ 存在，定义函数 
>
> $$h(x)=\left\{\begin{aligned}
&f[x,x_j], && x \ne x_j, \\ 
&f^{\prime}(x_j), &&x= x_j, 
\end{aligned}\right.$$
>
> 则 $h(x)$ 是关于 $x\in[a,b]$ 的连续函数．

**证明：** 因为 $\lim\limits_{x\to x_j}h(x)=\lim\limits_{x\to x_j}\dfrac{f(x)-f(x_j)}{x-x_j}=f'(x_j)=h(x_j)$，所以 $h(x)$ 在 $x=x_j$ 连续；而 $f\in C[a,b]$，则 $h(x)$ 是关于 $x\in[a,b]$ 的连续函数．  $\square$

{: .theorem}
> **定理4：** 
> 
> 设 $f'\in C[a,b]$，$f^{\prime\prime}$ 在 $x_j\in[a,b]$ 的一个邻域内连续，则定理 3 中的 $h\in C^1[a,b]$．

当 $x\ne x_j$ 时，

$$h'(x)=\dfrac{\mathrm{d}f[x,x_j]}{\mathrm{d}x}
=\dfrac{\mathrm{d}}{\mathrm{d}x}\left(\dfrac{f(x)-f(x_j)}{x-x_j}\right) 
=\dfrac{f'(x)(x-x_j)-[f(x)-f(x_j)]}{(x-x_j)^2}.$$

由 L'hospital 法则，

$$\begin{aligned}
\lim\limits_{x\to x_j}h'(x)&=\lim\limits_{x\to x_j}\dfrac{f'(x)(x-x_j)-[f(x)-f(x_j)]}{(x-x_j)^2} \\
&=\lim\limits_{x\to x_j}\dfrac{f^{\prime\prime}(x)(x-x_j)}{2(x-x_j)}=\dfrac{f^{\prime\prime}(x_j)}{2},
\end{aligned}$$

（上式用到了 $f^{\prime\prime}(x)$ 在 $x_j$ 的邻域连续）

以及

$$\begin{aligned}
h'(x_j)&=\lim\limits_{x\to x_j}\dfrac{h(x)-h(x_j)}{x-x_j} \\
&=\lim\limits_{x\to x_j}\dfrac{f[x,x_j]-f'(x_j)}{x-x_j} \\
&=\lim\limits_{x\to x_j}\dfrac{f(x)-f(x_j)-f'(x_j)(x-x_j)}{(x-x_j)^2} \\
&=\lim\limits_{x\to x_j}\dfrac{f'(x)-f'(x_j)}{2(x-x_j)}=\dfrac{f^{\prime\prime}(x_j)}{2},
\end{aligned}$$

所以 $h'(x_j)=\lim\limits_{x\to x_j}h'(x)$，故 $h'(x)$ 在 $x=x_j$ 处连续．

再由 $f'\in C[a,b]$ 得 $h'\in C[a,b]$，即 $h\in C^1[a,b]$．  $\square$

{: .theorem}
> **定理5（习题二第13题）**
> 
> 设 $a=x_0 < x_1 < x_2 < \cdots < x_{n-1} < x_n=b$，函数 $f(x)\in C^1[a,b]$，则差商
> 
> $$g(x):=f[x,x_0,x_1,\cdots,x_n]$$
> 
> 关于 $x$ 在 $[a,b]$ 上连续．这里 $g(x)$ 在节点 $x_k$ 上的值是通过重节点差商来定义的．进一步，若 $f(x)\in C^2[a,b]$，则有
> 
> $$g'(x)=f[x,x,x_0,x_1,\cdots,x_n],$$
> 
> 且 $g'(x)$ 也关于 $x$ 在 $[a,b]$ 上连续．


由引理 2，当 $x\ne x_j$ 时，

$$g(x)=\sum\limits_{j=0}^n\dfrac{f[x,x_j]}{\prod\limits_{\substack{k=0 \\ k\ne j}}^n(x_j-x_k)}.$$

为了让 $g(x)$ 在节点 $x_0,x_1,\cdots,x_n$ 处定义合理，约定

$$f[x,x_j]:=h_j(x)=\left\{\begin{aligned}
&f[x,x_j], && x \ne x_j, \\ 
&f'(x_j), &&x= x_j, 
\end{aligned}\right.$$

（1）由 $f\in C^1[a,b]$，只需证明 $g$ 在 $x_0,x_1,\cdots,x_n$ 处的连续性．由定理 3，$h_j\in C[a,b]$，而 $g(x)$ 是 $h_0,h_1,\cdots,h_n$ 的线性组合，故 $g\in C[a,b]$．

（2）首先

$$\begin{aligned}
f[x,x,x_0,x_1,\cdots,x_n]&=\lim\limits_{y\to x}f[x,x_0,x_1,\cdots,x_n,y] \\
&=\lim\limits_{y\to x}\dfrac{f[y,x_0,x_1,\cdots,x_n]-f[x,x_0,x_1,\cdots,x_n]}{y-x} \\
&=\lim\limits_{y\to x}\dfrac{g(y)-g(x)}{y-x}=g'(x).
\end{aligned}$$

若 $f(x)\in C^2[a,b]$，由定理 4 得 $h_j\in C^1[a,b]$，而  $g(x)$ 是 $h_0,h_1,\cdots,h_n$ 的线性组合，故 $g\in C^1[a,b]$． $\square$

### 注记

(1) 上面的 L'Hospital 法则的步骤可换为用 Taylor 公式．

(2) 证明的关键是在节点处补充定义以确保连续性．

### 错解 1

直接写“显然，$g\in C[a,b]$”，没有去证明 $g$ 在 $x_i$ 处的连续性，缺乏论证过程．

### 错解 2

写 $g'(x)=\dfrac{g(x)-g(x_0)}{x-x_n}$，可能是笔误．

写 $g'(x)=\dfrac{g(x)-g(x_0)}{x-x_0}$，少写了 lim．


## 第15题

{: .problem}
> 证明：对 $k=0,1,\cdots,n-2$，
>
> $$\sum\limits_{i=1}^n\dfrac{i^k}{(i-1)\cdots(i-i+1)(i-i-1)\cdots(i-n)}=0.$$

**方法一：** 考虑 $f(x)=x^{k+1}$ 在点 $(1,f(1)),\cdots,(n,f(n))$ 的插值多项式 $p(x)$．将 $p(x)$ 的表达式写出来：

$$p(x)=\sum\limits_{i=1}^n\dfrac{i^{k+1}(x-1)\cdots(x-i+1)(x-i-1)\cdots(x-n)}{(i-1)\cdots(i-i+1)(i-i-1)\cdots(i-n)}.$$

根据 Lagrange 插值余项公式或代数基本定理，$f(x)=p(x)$ 恒成立．

令 $x=0$ 得

$$0=f(0)=p(0)=\sum\limits_{i=1}^n\dfrac{(-1)^{n-1}n!\cdot i^k}{(i-1)\cdots(i-i+1)(i-i-1)\cdots(i-n)}.$$


**方法二：** 设 $f(x)=x^{k+1}$，$w_{n+1}(x)=(x-0)(x-1)\cdots(x-n)$，则

$$w_{n+1}'(x)=\sum\limits_{k=0}^n\prod\limits_{j\ne k}(x-j).$$

所以 $w_{n+1}'(i)=i(i-1)\cdots(i-i+1)(i-i-1)\cdots(i-n)$．

依据讲义的命题 2.3.1 中 (2.3.5) 式，

$$f[0,1,\cdots,n]=\sum\limits_{i=1}^n\dfrac{i^k}{(i-1)\cdots(i-i+1)(i-i-1)\cdots(i-n)}.$$

利用 Newton 差商的误差公式（讲义的(2.3.9)式）

$$f[0,1,\cdots,n]=\dfrac{f^{(n)}(\xi)}{n!}.$$

而 $\deg f \le n-1$，故 $f^{(n)}(\xi)=0$．

**【注1】** 最后也可以根据习题二的第 11 题，因为 $\deg f < n$，所以 $f[0,1,\cdots,n]=0$．

**【注2】** 也可以设 $f(x)=x^k$ 然后考虑 $f[1,2,\cdots,n]$．

## 第17题

{: .problem}
> 设 $n$ 次多项式 $f(x)$ 有互异的 $n$ 个实根 $x_1,x_2,\cdots,x_n$，证明
>
> $$\sum\limits_{i=1}^n\dfrac{x_i^k}{f'(x_i)}=\left\{\begin{aligned}
&0, && 0\le k\le n-2; \\
&a_n^{-1}, && k=n-1.
\end{aligned}\right.$$
>
> 其中 $a_n$ 为 $f(x)$ 的最高次项系数．

记

$$f(x)=a\prod\limits_{j=1}^n(x-x_j),$$

先写出 $f'(x)$ 的表达式，取 $x=x_i$，得到

$$f'(x_i)=a\prod\limits_{j\ne i}(x_i-x_j)$$

发现它跟Lagrange插值多项式很像．接下来利用第6题的结论或证明过程．

### 错解 1

没有写第 15 题，而写由题 15 知，$k=0,1,\cdots,n-2$ 时，$\sum\limits_{i=1}^n\dfrac{x_i^k}{f'(x_i)}=0$．

错因：对 Lagrange 插值多项式的性质不熟悉，第 15 题只是第 17 题的一种特殊情形，还是希望你能用 Lagrange 插值多项式的性质完整书写过程，以达到巩固的目的．



## 第19题

{: .problem}
> 已知 $f(x)$ 的函数值 $f(0)=3$, $f(1)=3$, $f(2)=\frac{5}{2}$，求 Newton 差商插值多项式 $N_2(x)$ ．再增加 $f(\frac{3}{2})=\frac{13}{4}$，求 $N_3(x)$．

用 Newton 插值多项式的递推式计算得

$$\begin{aligned}
N_2(x)&=3-\dfrac{1}{4}x(x-1), \\
N_3(x)&=3-\dfrac{1}{4}x(x-1)-\dfrac{7}{6}x(x-1)(x-2).
\end{aligned}$$


## 第20题

{: .problem}
> 已知函数 $y=f(x)$ 的观测数据为 $f(0)=1$, $f(1)=2$, $f(2)=4$, $f(3)=8$，试分别求出三次 Newton 前差和后差插值多项式，并求 $f(0.25)$ 和 $f(2.5)$ 的近似值．

三次Newton前差和后差插值多项式分别是

$$\begin{aligned}
N_3(x)&=N_3(0+s)=1+s+\dfrac{1}{2}s(s-1)+\dfrac{1}{6}s(s-1)(s-2), \\
N_3(x)&=N_3(3+t)=8+4t+t(t+1)+\dfrac{1}{6}t(t+1)(t+2).
\end{aligned}$$

这两个多项式是相同的（替换 $t=x-3$，$s=x-0$ 之后）

取 $s=0.25$，$t=-2.75$，都能算出 $N_3(0.25)=\dfrac{155}{128}$．

取 $s=2.5$，$t=-0.5$，都能算出 $N_3(2.5)=\dfrac{91}{16}$．









