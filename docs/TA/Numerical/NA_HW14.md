---
layout: default
title: 第14周作业
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

# 第14周作业

教材习题10：27、29、30、35（2）

# 解答

## 第27题

{: .problem}
> 应用 $k=1$ 的显式和隐式 Adams 方法的 PECE 模式解初值问题
>
> $$y'=-y+t+1,\quad 0\le t\le 1,\quad y(0)=1.$$
>
> 取步长 $h=0.2$，用经典的四阶 Runge-Kutta 方法提供出发值．

直接代入 Runge-Kutta 方法得到 $y_1$，然后用 Adams 方法得到 $y_2,y_3,y_4,y_5$ 即可．


## 第29题

{: .problem}
> 试从
>
> $$y(t_{n+1})-y(t_{n-p}) = \int_{t_{n-p}}^{t_{n+1}}f(t,y(t))\mathrm{d}t = \int_{t_{n-p}}^{t_{n+1}}y'(t)\mathrm{d}t$$
>
> 导出解初值问题
>
> $$y'=f(t,y), \quad a\le t\le b, \quad y(a)=y_0$$
>
> 的 Nystrom 方法：
>
> $$y_{n+1}=y_{n-1}+2hf_n.$$

对 $y'(t)=f(t,y(t))$ 在区间 $[t_{n-1},t_{n+1}]$ 两端积分可得

$$y(t_{n+1})-y(t_{n-1})=\int_{t_{n-1}}^{t_{n+1}}f(t,y(t))\mathrm{d}t.$$

根据中点矩形公式，

$$\int_{t_{n-1}}^{t_{n+1}}f(t,y(t))\mathrm{d}t \approx (t_{n+1}-t_{n-1})f(t_n,y(t_n)).$$

所以得到 Nystrom 方法 

$$y_{n+1}=y_{n-1}+2hf_n.$$


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








