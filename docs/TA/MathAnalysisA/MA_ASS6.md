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

进而推导出$f(x)$恒为$0$.


{% endraw %}
