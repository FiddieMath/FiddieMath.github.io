---
layout: default
title: 第16周作业（理论13） 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 13
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

# 第 16 周作业（理论13）

第五章 28、30、32、35(2)



## 第28题

{: .problem}
> 用算法 5.1 （四阶 Adams 预测-校正方法）解初值问题
>
> $$y'=\dfrac{1}{t}(y^2+y), \qquad 1\le t\le 3, \qquad y(1)=-2.$$
>
> 取步长 $h=0.5$．

$$\begin{array}{c | cc}
\hline n & t_n & y_n \\
\hline 0 & 1 & -2 \\
1 & 1.5 & -1.49540883 \\
2 & 2.0 & -1.33056041 \\
3 & 2.5 & -1.24804611 \\
4 & 3.0 & -1.17988463 \\ \hline
\end{array}$$



## 第30题

{: .problem}
> 试用待定系数法导出 Milne 方法的校正公式：
>
> $$y_{n+1}=y_{n-1}+\dfrac{h}{3}\Big(f(t_{n+1},y_{n+1})+4f(t_n,y_n)+f(t_{n-1},y_{n-1})\Big)$$

对 $y'(t)=f(t,y(t))$ 在区间 $[t_{n-1},t_{n+1}]$ 两端积分可得

$$y(t_{n+1})-y(t_{n-1})=\int_{t_{n-1}}^{t_{n+1}}f(t,y(t))\mathrm{d}t.$$

我们假设 $f_n$ 为 $f(t_n,y(t_n))$，以及

$$\int_{t_{n-1}}^{t_{n+1}}f(t,y(t))\mathrm{d}t\approx h(Af_{n+1}+Bf_n+Cf_{n-1}).$$

对数值积分公式求系数可以用待定系数法，我们令 $f(t,y(t))=1, t-t_n, (t-t_n)^2$ 使得上面的约等号变成等号，可得

$$\left\lbrace\begin{aligned}
2h&=h(A+B+C), \\
0&=h(Ah-Ch), \\
\tfrac{2}{3}h^3&=h(Ah^2+Ch^2).
\end{aligned}\right. \Rightarrow \left\lbrace\begin{aligned}
A&=\tfrac{1}{3}, \\
B&=\tfrac{4}{3}, \\
C&=\tfrac{1}{3}.
\end{aligned}\right.$$

于是我们就得到了Milne方法校正公式．



## 第32题

{: .problem}
> 证明 $m$ 阶齐次线性差分方程 
>
> $$a_0(n)y(n)+a_1(n)y(n+1)+\cdots+a_m(n)y(n+m)=0$$
>
>  至少有 $m$ 个线性无关解．

取定前 $m-1$ 个初始值 $y(0),y(1),\cdots,y(m-1)$ 后，从 $y(m)$ 开始的值均可由差分方程递推式给出．

取 $m$ 组初始值 $y(0)=1$, $y(1)=\cdots=y(m-1)=0$；$y(0)=0$, $y(1)=1$, $y(2)=\cdots=y(m-1)=0$；$\cdots$；$y(0)=y(1)=\cdots=y(m-2)=0$, $y(m-1)=1$ 分别得到的解 $y_1(n)$, $y_2(n)$, $\cdots$, $y_m(n)$ 线性无关，这是因为矩阵

$$Y=\lbrace y_k(n)\rbrace_{n=0,1,\cdots,m-1; k=1,2,\cdots,m} \in \mathbb{F}^{m\times m}$$

是对角矩阵 $\mathrm{diag}\lbrace 1,1,\cdots,1\rbrace$，秩为 $m$．

## 第35(2)题

{: .problem}
> 求差分方程：
>
> $$y(n+2)+2y(n+1)+2y(n)=2^n$$
>
> 的通解．

这题很重要，你懂的．首先特征方程为

$$\lambda^2+2\lambda+2=0,$$

解得 $\lambda=-1\pm\mathrm{i}$．所以有两个线性无关通解：

$$(\sqrt{2})^n\cos\dfrac{3n\pi}{4}, \qquad (\sqrt{2})^n\sin\dfrac{3n\pi}{4}.$$

假设有特解 $y^*(n) = a\cdot 2^n$，则代入差分方程得

$$a\cdot 2^{n+2}+2a\cdot 2^{n+1}+2a\cdot 2^n=2^n,$$

解得 $a=\dfrac{1}{10}$．所以有一个特解 $y^*(n)=\dfrac{1}{10}\times 2^n$．

综上，差分方程的通解是

$$y(n)=\dfrac{1}{10}\times 2^n+C_1(\sqrt{2})^n\cos\dfrac{3n\pi}{4}+C_2(\sqrt{2})^n\sin\dfrac{3n\pi}{4}.$$

其中，$C_1,C_2$ 是实常数．


