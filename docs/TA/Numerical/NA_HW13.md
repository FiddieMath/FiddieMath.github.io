---
layout: default
title: 第13周作业
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

{: .new}
> 第 8、9、10、11、12 周的作业评估近期会补全．

# 第13周作业

教材习题10：4、7、11、13、15、18、21、23

# 解答

## 第4题

{: .problem}
> 用 Taylor 级数法（取 $p=3$ ）导出求解初值问题
>
> $$y'=\dfrac{1}{1+y^2}, \quad y(0)=1$$
>
> 的数值方法．

解：设 $f(t,y(t)) = \dfrac{1}{1+y^2}$，则 $y'(t)=f(t,y(t))$．依 Taylor 展开，

$$y(t+h)=y(t)+hy'(t)+\dfrac{1}{2}h^2y^{\prime\prime}(t)+\dfrac{1}{3!}h^3y^{(3)}(t)
+\cdots,$$

其中，

$$\begin{aligned}
y'(t) &= f(t,y(t)), \\
y^{\prime\prime}(t) &= f_t(t,y(t)) + y'(t)f_y(t,y(t)) = f_t + ff_y, \\
y^{(3)}(t) &= \Big[f_{tt}(t,y(t)) + y'(t)f_{ty}(t,y(t))\Big] + \\
&\qquad y^{\prime\prime}(t)f_y(t,y(t)) + y'(t)\Big[ f_{ty}(t,y(t)) + f_{yy}(t,y(t))y'(t)\Big] \\
&=f_{tt}+2y'f_{ty}+y^{\prime\prime}f_y+(y')^2f_{yy} \\
&=f_{tt}+2ff_{ty}+(f_t+ff_y)f_y+f^2f_{yy}.
\end{aligned}$$

代入 $f$ 的表达式，得

$$\begin{aligned}
f_y&=-\dfrac{2y}{(1+y^2)^2}, \\
f_{yy}&=\dfrac{6y^2-2}{(1+y^2)^3}, \\
y'(t)&=\dfrac{1}{1+y^2}, \\
y^{\prime\prime}(t)&=\dfrac{-2y}{(1+y^2)^3}, \\
y^{(3)}(t)&=\dfrac{4y^2}{(1+y^2)^5}+\dfrac{6y^2-2}{(1+y^2)^5} = \dfrac{10y^2-2}{(1+y^2)^5}.
\end{aligned}$$

将 $y',y^{\prime\prime},y^{(3)}$ 代回原式，并取 $h = t_{n+1}-t_n$，得迭代公式

$$\begin{aligned}
y_0&=1, \\
y_{n+1}&=y_n+h\left[\dfrac{1}{1+y_n^2}-\dfrac{hy_n}{(1+y_n^2)^3} + \dfrac{h^2}{3}\cdot\dfrac{5y_n^2-1}{(1+y_n^2)^5}\right].
\end{aligned}$$

{: .warning}
> 可能到了后半学期了，同学们学习稍有松懈，推导出了错误的公式，比如
>
> $$y_{n+1}=y_n+h[f(y_n)+\dfrac{1}{2}h(f'(y_n)f(y_n)) + \dfrac{1}{3!}h^2(f^{\prime\prime}(y_n)f^2(y_n))$$
>
> 然后就照抄答案．请确保理解了书中 $f=f(t,y(t))$ 的具体含义！

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


## 第11题

{: .problem}
> 试证明，用变形的 Euler 方法，改进的 Euler 方法和 Heun 方法解初值问题
>
> $$y'=y+t+1, \quad 0\le t\le 1, \quad y(0)=1,$$
>
> 对任意的 $h$ 值得到的近似解都是相同的．能否把这个结论推广到微分方程为 $y'=ay+bt+c$ 的情形 （$a,b,c$ 都是常数）？

代入三种方法的格式，都能推出

$$y_{n+1}=\left(1-h+\dfrac{1}{2}h^2\right)y_n+\left(h-\dfrac{1}{2}h^2\right)t_n+h.$$

一般情形：

$$y_{n+1}=\left(1+ah+\dfrac{1}{2}a^2h^2\right)y_n+\left(\dfrac{ab}{2}h^2+bh\right)t_n+\dfrac{ac+b}{2}h^2+ch.$$

{: .new}
> 应当注意到，变形的 Euler 方法，改进的 Euler 方法和 Heun 方法都属于二阶 Runge-Kutta 法．事实上，对于微分方程
>
> $$y'=ay+bt+c,$$
>
> 所有二阶 Runge-Kutta 方法都将导出相同的差分格式．


## 第13题

{: .problem}
> 试证明，解初值问题
>
> $$y'=f(t,y), \quad y(t_0)=\eta$$
>
> 的隐式单步法
>
> $$y_{n+1}=y_n+\dfrac{1}{6}h[4f(t_n,y_n)+2f(t_{n+1},y_{n+1})+hf'(t_n,y_n)]$$
>
> 为三阶方法．

依据 $p$ 阶方法的定义（$p=3$），本题需要验证

$$y(t+h)=y(t)+\dfrac{1}{6}h[4f(t,y(t))+2f(t+h,y(t+h))+h\dfrac{\mathrm{d}}{\mathrm{d}t}f(t,y(t))]+O(h^4).$$

首先，由 $y'=f(t,y)$，得

$$\begin{aligned}
y^{\prime\prime}&=\dfrac{\mathrm{d}}{\mathrm{d}t}f(t,y(t))=f_t+ff_y, \\
y^{(3)}&=f_{tt}+2ff_{ty}+(f_t+ff_y)f_y+f^2f_{yy}.
\end{aligned}$$

依 Taylor 展开，

$$\begin{aligned}
y(t+h)-y(t)&=hy'(t)+\dfrac{h^2}{2}y^{\prime\prime}(t)+\dfrac{h^3}{6}y^{(3)}(t) + O(h^4) \\
&=hf+\dfrac{h^2}{2}(f_t+ff_y)+\dfrac{h^3}{6}\Big[f_{tt}+2ff_{ty}+(f_t+ff_y)f_y+f^2f_{yy}\Big] +O(h^4).
\end{aligned}$$

所以

$$\begin{aligned}
f(t+h,y(t+h))&=f(t,y(t)) + [hf_t(t,y(t)) + (y(t+h)-y(t))f_y(t,y(t))]  \\
&\qquad + \dfrac{1}{2!}[h^2f_{tt}(t,y(t))+2h(y(t+h)-y(t))f_{ty}(t,y(t)) + (y(t+h)-y(t))^2f_{yy}(t,y(t))] \\
&=f+h(f_t+ff_y)+\dfrac{h^2}{2}(f_t+ff_y)f_y + \dfrac{h^2}{2}[f_{tt}+2ff_{ty}] + O(h^3),
\end{aligned}$$

所以

$$\begin{aligned}
&\quad\,\,y(t+h)-y(t)-\dfrac{1}{6}h[4f(t,y(t))+2f(t+h,y(t+h))+h\dfrac{\mathrm{d}}{\mathrm{d}t}f(t,y(t))] \\
&=hf+\dfrac{h^2}{2}(f_t+ff_y)+\dfrac{h^3}{6}\Big[f_{tt}+2ff_{ty}+(f_t+ff_y)f_y+f^2f_{yy}\Big]  \\
&\qquad -\Big[\dfrac{2}{3}hf + \dfrac{1}{3}h\Big[f+h(f_t+ff_y)+\dfrac{h^2}{2}(f_t+ff_y)f_y+\dfrac{h^2}{2}[f_{tt}+ff_{ty}]\Big]
+\dfrac{h^2}{6}(f_t+ff_y) \Big] +O(h^4) \\
&=O(h^4).
\end{aligned}$$

{: .new}
> 上述做法是直接用多元函数 Taylor 展开来计算的．本题也可以用提示（习题4，第36题）进行推导，对插值误差公式两边进行积分．

## 第15题

{: .problem}
> 试写出经典的四阶 Runge-Kutta 方法解初值问题
>
> $$y'=f(t), \quad t_0\le t\le T, \quad y(t_0)=y_0$$
>
> 的计算公式．它与数值积分公式有什么关系？

公式为：$y_0=y(t_0)$，

$$y_{n+1}=y_n+\dfrac{h}{6}\left[f(t_n)+4f\left(t_n+\dfrac{h}{2}\right)+f(t+h)\right], \quad n=0,1,\cdots,N-1.$$

其中，$t_n=t_0+nh$，$h=\dfrac{T-t_0}{N}$，$n=0,1,\cdots,N$．

可以发现，$y_{n+1}-y_n$ 就是计算积分 $\int_{t_n}^{t_{n+1}}f(t)\mathrm{d}t$ 的 Simpson 公式．

## 第18题

{: .problem}
> 试证明，用 Euler 方法解初值问题
>
> $$y'=at+b, \quad y(0)=0$$
>
> 得到的解为
>
> $y_n=\dfrac{1}{2}at_n^2+bt_n-\dfrac{1}{2}aht_n$，
>
> 其中 $t_n=nh$，并证明方法是收敛的．

可以算出原问题的精确解是 $y(t)=\dfrac{1}{2}at^2+bt$，所以固定 $t_n$ 后，

$$y(t_n)-y_n=\dfrac{1}{2}aht_n \to 0(h\to 0).$$

从而方法是收敛的．

## 第21题

{: .problem}
> 求变形的 Euler 方法（中点方法）
> 
> $$y_{n+1}=y_n+hf\left(t_n+\dfrac{h}{2},y_n+\dfrac{h}{2}f(t_n,y_n)\right)$$
>
> 和改进的 Euler 方法的绝对稳定区间．

分析绝对稳定区间只需考虑将方法用于 $y'=\mu y$ 的增长因子 $\mu h$ 的取值范围．

对于变形的 Euler 方法，格式化为

$$y_{n+1}=(1+\mu h+\dfrac{(\mu h)^2}{2})y_n,$$

解不等式 $\left\vert 1+\mu h+\dfrac{(\mu h)^2}{2}\right\vert < 1$，得

$$\mu h\in (-2,0).$$

对于改进的 Euler 方法，得到的也是

$$y_{n+1}=(1+\mu h+\dfrac{(\mu h)^2}{2})y_n,$$

所以绝对稳定区间都是 $(-2,0)$．

{: .warning}
> 有个别同学不清楚绝对稳定区间的定义是什么，得到了一些奇怪的结果．


## 第23题

{: .problem}
> 应用 Heun 方法
>
> $$y_{n+1} = y_n+\dfrac{h}{4}\left[f(t_n,y_n)+3f\left(t_n+\dfrac{2}{3}h,y_n+\dfrac{2}{3}hf(t_n,y_n)\right)\right]$$
>
> 解初值问题
>
> $$y'=-y, \quad y(0)=y_0$$
>
> 时，问步长 $h$ 应取何值方能保证方法的绝对稳定性？

首先对 $y'=\mu y$，Heun 方法化为

$$y_{n+1}=(1+\mu h+\dfrac{(\mu h)^2}{2})y_n,$$

前一题已经求出绝对稳定区间为 $\mu h\in(-2,0)$．当 $\mu=-1$ 时，$h\in(0,2)$ 时，Heun 方法稳定性可保证．










