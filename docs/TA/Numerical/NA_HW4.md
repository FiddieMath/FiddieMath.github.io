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

对 $m$ 用数学归纳法来证明．

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

下面的解答需要用到习题二的第 6 题：

{: .lemma}
> **引理 1：** $\sum\limits_{j=0}^n\prod\limits_{\substack{k=0 \\ k\ne j}}^n\dfrac{x-x_k}{x_j-x_k}=1$

**证明：** 考虑常值函数 $f(x)=1$ 的 Lagrange 插值多项式，应用代数基本定理或 Lagrange 插值多项式的余项公式即可得结论．

{: .lemma}

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
> $h(x)=\left\{\begin{aligned}
&f[x,x_j], && x \ne x_j, \\ 
&f^{\prime}(x_j), &&x= x_j, 
\end{aligned}\right.$ 
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
&=\lim\limits_{x\to x_j}\dfrac{f''(x)(x-x_j)}{2(x-x_j)}=\dfrac{f''(x_j)}{2},
\end{aligned}$$

（上式用到了 $f''(x)$ 在 $x_j$ 的邻域连续）

以及

$$\begin{aligned}
h'(x_j)&=\lim\limits_{x\to x_j}\dfrac{h(x)-h(x_j)}{x-x_j} \\
&=\lim\limits_{x\to x_j}\dfrac{f[x,x_j]-f'(x_j)}{x-x_j} \\
&=\lim\limits_{x\to x_j}\dfrac{f(x)-f(x_j)-f'(x_j)(x-x_j)}{(x-x_j)^2} \\
&=\lim\limits_{x\to x_j}\dfrac{f'(x)-f'(x_j)}{2(x-x_j)}=\dfrac{f''(x_j)}{2},
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
