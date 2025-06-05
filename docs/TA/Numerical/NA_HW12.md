---
layout: default
title: 第14-15周作业（理论12） 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 12
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

# 第 14-15 周作业（理论12）

第五章 7、8、12、13、15、17、23


## 第7题

{: .problem}
> 对初值问题
>
> $$y'=\dfrac{1}{1+y^2},0\le t\le 1, \quad y(0)=1$$
>
> 求 Euler 方法的整体离散误差界．

本题即估计 

$$\varepsilon_n = y(t_n) - y_n$$

的一致上界．书中已经证明

$$\max\limits_{0\le n\le N}\vert \varepsilon_n\vert \le \dfrac{h\Vert y^{\prime\prime}\Vert_{\infty}}{2L}(\mathrm{e}^{L(b-a)}-1).$$

因为对 $f(t,y)=\dfrac{1}{1+y^2}$，

$$\max\limits_{x\in[0,1]}\vert f'\vert=\max\limits_{x\in[0,1]}\left\vert\dfrac{-2y}{(1+y^2)^2}\right\vert = \dfrac{1}{2},$$

$$\max\limits_{x\in[0,1]}\vert y^{\prime\prime}\vert=\max\limits_{x\in[0,1]}\left\vert\dfrac{-2y}{(1+y^2)^3}\right\vert = \dfrac{1}{4},$$

所以 $L = \dfrac{1}{2}$，$\Vert y^{\prime\prime}\Vert_{\infty} = \dfrac{1}{4}$．

代入 $a=0$，$b=1$，可得

$$\max\limits_{0\le n\le N}\vert \varepsilon_n\vert \le \dfrac{h}{4}(\sqrt{\mathrm{e}}-1).$$

{: .warning}
> 只要得到的上界是 $h$ 的常数倍都没问题．有同学漏了 $h$，放出来 $\vert \varepsilon_n\vert$ 的一致上界是常数．


## 第8题

{: .problem}
> 试用改进的 Euler 方法解初值问题
>
> $$y'=t+y, \quad 0\leqslant t\leqslant 1, \quad y(0)=1,$$
>
> 取步长 $h=0.2$，并将计算结果与精确值比较．

精确值：$y(t)=2\mathrm{e}^t-t-1$．

改进的 Euler 方法：

$$\begin{aligned}
&y_{n+1}^{(0)}=y_n+hf(t_n,y_n), \\
&y_{n+1}=y_n+\dfrac{h}{2}[f(t_n,y_n)+f(t_{n+1},y_{n+1}^{(0)})] \\
&y_0=y_a, \quad n=0,1,\cdots,N-1.
\end{aligned}$$

代入 $f(t,y)=t+y$ 得迭代格式

$$\begin{aligned}
y_0&=1, \\
y_{n+1}^{(0)}&=y_n+ht_n+hy_n, \\
y_{n+1}&=y_n+\dfrac{h}{2}(t_n+y_n+t_{n+1}+y_{n+1}^{(0)}) \\
&=y_n+\dfrac{h}{2}(t_n+y_n+t_{n+1}+y_n+ht_n+hy_n) \\ 
&=\left(1+h+\dfrac{h^2}{2}\right)y_n + \dfrac{1}{2}\left(n+\dfrac{1}{2}\right)h^2+\dfrac{1}{2}nh^3.
\end{aligned}$$

其中 $n=0,1,2,3,4$．解得 

$$\begin{aligned}
y_1&=1.24, \\
y_2&=1.5768, \\
y_3&=2.031696, \\
y_4&=2.63066912, \\
y_5&=3.405416326.
\end{aligned}$$

与精确值作比较，可发现整体误差在 $10^{-2}$ 的量级．


## 第12题

{: .problem}
> 试验证解初值问题
>
> $$y'=f(t,y), \qquad y(t_0)=\eta$$
>
> 的数值公式
>
> $$y_{n+1}=y_n+\dfrac{h}{2}(f(t_n,y_n)+f(t_{n+1},y_{n+1}))$$
>
> 对 $y(t)=1,t,t^2$ 均准确成立，但对 $y(t)=t^3$ 不准确成立，并说明理由．

这个数值公式是梯形方法，它是二阶方法，局部离散误差为 $-\dfrac{h^3}{12}y^{(3)}(\xi_n)$，所以对 $y(t)=1,t,t^2$ 准确成立，但不是对 $y(t)=t^3$ 准确成立．


## 第13题

{: .problem}
> 试证明，解初值问题
>
> $$y'=f(t,y), \qquad y(t_0)=\eta$$
>
> 的隐式单步法
>
> $$y_{n+1}=y_n+\dfrac{h}{6}[4f(t_n,y_n)+2f(t_{n+1},y_{n+1})+hf'(t_n,y_n)]$$
>
> 为三阶方法．

**思路1：** 将 $y(t_{n+1})$ 和 $f(t_{n+1},y(t_{n+1}))$ 在 $t=t_n$ 处作 Taylor 展开，注意

$$\begin{gathered}
y^{\prime\prime}=f_t+f_yf, \\
y^{(3)}=f_{tt}+2f_{ty}f+f_{yy}f^2+f_y(f_t+f_yf),
\end{gathered}$$

比较等号两侧 $h$, $h^2$ 项系数即可得它是三阶方法．


**思路2：** 将 $y'=f(t,y)$ 在 $t\in [t_n,t_{n+1}]$ 上积分，可得

$$y(t_{n+1})-y(t_n)=\int_{t_n}^{t_{n+1}}f(t,y(t))\mathrm{d}t.$$

利用 Hermite 插值公式来离散 $f(t_n,y_n)$，$f'(t_n,y_n)$，$f(t_{n+1},y_{n+1})$， 处理右端积分中的被积函数，代入 Hermite 插值的误差公式可推导得局部离散误差为 $-\dfrac{h^4}{72}y^{(4)}(\xi_n)$．


## 第15题

{: .problem}
> 试写出经典的四阶Runge-Kutta方法解初值问题
>
> $$y'=f(t), \qquad t_0\le t\le T, \quad y(t_0)=y_0$$
>
> 的计算公式．它与数值积分公式有什么关系？


$$y(t_{n+1})-y(t_n)=\int_{t_n}^{t_{n+1}}y'\mathrm{d}t=\int_{t_n}^{t_{n+1}}f(t)\mathrm{d}t.$$

注意 $f(t)$ 与 $y$ 无关，所以将四阶 RK 方法代入可得

$$y_{n+1}-y_n=\dfrac{h}{6}\left[f(t_n)+4f(t_n+\frac{h}{2})+f(t_n+h)\right],$$

其中 $t_n=nh$．可以发现上式右端恰为积分 $\displaystyle \int_{t_n}^{t_{n+1}}f(t)\mathrm{d}t$ 的 Simpson 求积公式．

当然，也可以写：在 $[0,T]$ 上积分（其中 $T=nh=t_n$ ），发现 $y_n-y_0$ 的右端表达式恰是复合 Simpson 公式．

**【错解】** 没有发现 $f$ 与 $y$ 无关，写出其它解释． 




## 第17题

{: .problem}
> 试证明经典四阶Runge-Kutta方法解初值问题
>
> $$y'=\lambda y, \qquad y(t_0)=y_0$$
>
> 的计算公式可写成
>
> $$y_{n+1}=\left(1+\lambda h+\frac{1}{2}(\lambda h)^2+\frac{1}{6}(\lambda h)^3+\frac{1}{24}(\lambda h)^4\right)y_n,$$
>
> 并就初值问题 
>
> $$y'=-10y, \qquad y(0)=1$$
>
> 求 $y(1)$ 的近似值．（取步长 $h=0.1$ ）

推导计算公式是简单的．

当 $\lambda = -10$，$h=0.1$ 时，$\lambda h=-1$，迭代格式成为

$$y_{n+1}=\dfrac{3}{8}y_n,$$

所以 $y(1)\approx y_{10}=(\dfrac{3}{8})^{10}$．



## 第23题

{: .problem}
> 用 Heun 方法
>
> $$y_{n+1}=y_n+\dfrac{h}{4}\left[f(t_n,y_n)+3f\left(t_n+\dfrac{2}{3}h,y_n+\dfrac{2}{3}hf(t_n,y_n)\right)\right]$$
>
> 解初值问题
>
> $$y'=-y, \qquad y(0)=y_0$$
>
> 时，问步长 $h$ 应取何值方能保证方法的绝对稳定性？

在 Heun 方法中代入 $f(t,y)=-y$ 可得

$$\begin{aligned}
y_{n+1}&=y_n+\dfrac{h}{4}\left[-y_n-3\left(y_n-\dfrac{2}{3}hy_n\right)\right] \\
&=\left(1-h+\dfrac{h^2}{2}\right)y_n,
\end{aligned}$$

令 

$$\left\vert 1-h+\dfrac{h^2}{2}\right\vert < 1,$$

解得 $0 < h < 2$．



