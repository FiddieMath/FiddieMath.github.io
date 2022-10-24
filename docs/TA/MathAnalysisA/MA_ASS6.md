---
layout: default
title: 第6次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 9
---

## 第6次作业

作业内容还不知道呢（知道的可以在群里说一声）

### 主要问题

{% raw %}

还没改，别急

### 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

{: .note }
> 回顾Lipschitz连续和Hölder连续的定义：
>
> 设$f$是区间$I$中的函数. 如果存在$0 < \alpha < 1$, 以及常数$M$, 使得
> 
> $$|f(x)-f(y)|\le M|x-y|^{\alpha}, \qquad \forall x,y\in I,$$
>
> 则称$f$是$I$中的$\alpha$阶Hölder函数, 记为$f\in C^{\alpha}(I)$. 
>
> 如果存在常数$L$, 使得
>
> $$|f(x)-f(y)|\le L|x-y|, \qquad \forall x,y\in I,$$
>
> 则称$f$为$I$中的Lipschitz函数, 记为$f\in \mathrm{Lip}(I)$.
>
> Hölder函数和Lipschitz函数都是一致连续的. 
>
> 本题我们探究如果把Hölder函数的$\alpha$设为$\alpha>1$会出现什么情况. 

**1.** 设$f$是定义在$(-\infty,+\infty)$上的函数, 满足

$$|f(x)-f(y)|\le(x-y)^{\alpha},  \qquad \forall x,y\in(-\infty,+\infty).$$

其中实数$\alpha>1$. 
证明：对任意的$x,y\in(-\infty,+\infty)$以及任意的正整数$n$, 都有

$$\vert f(x)-f(y)\vert \le \dfrac{1}{n^{\alpha-1}}\vert x-y\vert^{\alpha}.$$

进而推导出$f(x)$必为常值函数.


{: .note }
> 下面的题可以用来巩固一下对“上确界”概念的理解.

{% raw %}
**2.** 设$E$是数集, 函数$f:E\to\mathbb{R}$. 定义函数$f$的**连续模(modulus of continuity)**为

$$\omega(\delta)=\sup\{|f(x_1)-f(x_2)|\,|x_1,x_2\in E, |x_1-x_2| < \delta\}$$

证明: 

(1)$\omega(\delta)$是单调不降的非负函数, 并且在$0$处存在右极限:

$$\omega(0^+)=\lim\limits_{\delta\to 0^+}\omega(\delta).$$

(2)对任意的$\varepsilon>0$, 存在$\delta > 0$, 使得对任意$x_1,x_2\in E$, 当$\vert x_1 - x_2 \vert < \delta$时, 有

$$|f(x_1)-f(x_2)| < \omega(0^+) + \varepsilon.$$

(3)若$E$是区间(例如: 闭区间、开区间、半开半闭区间), 则

$$\omega(\delta_1+\delta_2) \le \omega(\delta_1) + \omega(\delta_2).$$

(4)设$E=\mathbb{R}$, 则函数$f(x)=x$的连续模为$\omega(\delta)=\delta(\forall \delta>0)$.

(5)设$E=\mathbb{R}$, 则函数$f(x)=\sin(x^2)$的连续模为$\omega(\delta)=2(\forall \delta>0)$.

(6)函数$f$在集合$E$上一致连续当且仅当$\omega(0^+)=0$. 


{% endraw %}
