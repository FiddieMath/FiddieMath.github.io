---
layout: default
title: 第13周作业（理论11） 
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

# 第 13 周作业（理论11）

第五章 3、4

# 解答

### 第3题解答

{: .problem}
> 假设函数 $g(x)$ 和 $h(x)$ 在区间 $[a,b]$ 上连续，证明初值问题
>
> $$y'=g(x)y+h(x), \qquad y(a)=\eta$$
>
> 在 $[a,b]$ 上有唯一解，并且对任何初始值都是适定的．

直接使用定理 5.1.1．


### 第4题解答

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
> 【易错警示】推导出了错误的公式，比如
>
> $$y_{n+1}=y_n+h[f(y_n)+\dfrac{1}{2}h(f'(y_n)f(y_n)) + \dfrac{1}{3!}h^2(f^{\prime\prime}(y_n)f^2(y_n))$$
>
> 请确保理解了书中 $f=f(t,y(t))$ 的具体含义！










