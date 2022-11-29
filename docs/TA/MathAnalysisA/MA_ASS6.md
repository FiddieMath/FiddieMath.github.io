---
layout: default
title: 第6次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 9
---

## 第6次作业

习题3.3/14

习题3.4/1, 3, 4, 5, 7, 9(2), 10, 12(只用讨论$M(x)$), 14.

### 主要问题

{% raw %}

## 批改记号

对于没有文字注释的批改部位，符号的意义如下：

| 记号         | 含义 |
|:-------------|:--------------------------------------------|
| $(A)$        | 建议不要随便使用未经证明的还没有学过的内容！ |
| $?$和下划线  | 此处跳跃过大，请用更细致明确的语言补充  |
| $\times$和下划线  | 此处推理存在错误 |
| $?$和双下划线  | 使用了未经说明的概念 |
| $?$和圈 | 使用了含混不清的概念或符号 |
| $\times$和圈 | 此处符号使用错误，不可以这么写！ |

## 问题

### 3.3.14题

$(1)$没解释为什么 $a>0$ 

### 3.4.9题

$(1)$ $\forall\varepsilon>0$, $\exists A$, 当 $x,y>A$ 时，取$\delta=\varepsilon/2$, 当$\vert x-y\vert <\delta$ 有 $\vert f(x)-f(y)\vert <\varepsilon$ , 从而$f(x)$在$[A,\infty)$上一致连续.

错误原因：$A$ 随$\varepsilon$ 而变动而变动.

### 3.4.10题

$(1)$ $\forall\varepsilon>0$ ,$\exists N$ ,使得$\forall x\geq N$, 有$\vert f(x)-\alpha\vert <\varepsilon/2$. 则$x\geq N$时，$\forall \varepsilon > 0$ , $\exists \delta$ ,当 $\vert x_1-x_2\vert <\delta$ 时，$\vert f(x_1)-f(x_2)\vert <\varepsilon$ .从而$f(x)$在$[N,\infty)$上一致连续.

错误原因：同上, $N$随$\varepsilon$变动而变动.

### 3.4.12题

$(1)$ 认为区间上的连续函数必定可以划分为一些小区间上的单调函数首尾相接.

错误原因：考虑$[-1,1]$上的函数

$$f(x)=\begin{cases}0&x=0\\\\x\sin \dfrac{1}{x} &\text{其他情况} \end{cases}$$

在$0$附近.

### 3.4.14题

$(1)$ 老生常谈的问题：反证法 $\lim_{x\to\infty}f(x)=\infty$ 的否定不是$\lim_{x\to+\infty}f(x)=\alpha$ 或$\lim_{x\to-\infty}f(x)=\beta$ ，也不是$f(x)$有界，还有极限不存在的可能.例子请自行寻找.




### 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.** 设$f:\mathbb{R}^+\to\mathbb{R}^+$是一致连续函数. 是否有

$$\lim\limits_{x\to+\infty}\dfrac{f(x+\frac{1}{x})}{f(x)}=1?$$

{: .note }
> 回顾Lipschitz连续和Hölder连续的定义：
>
> 设$f$是区间$I$中的函数. 如果存在$0 < \alpha < 1$, 以及常数$M$, 使得
> 
> $$\vert f(x)-f(y)\vert \le M\vert x-y\vert ^{\alpha}, \qquad \forall x,y\in I,$$
>
> 则称$f$是$I$中的$\alpha$阶Hölder函数, 记为$f\in C^{\alpha}(I)$. 
>
> 如果存在常数$L$, 使得
>
> $$\vert f(x)-f(y)\vert \le L\vert x-y\vert , \qquad \forall x,y\in I,$$
>
> 则称$f$为$I$中的Lipschitz函数, 记为$f\in \mathrm{Lip}(I)$.
>
> Hölder函数和Lipschitz函数都是一致连续的. 
>
> 本题我们探究如果把Hölder函数的$\alpha$设为$\alpha>1$会出现什么情况. 

**2.** 设$f$是定义在$(-\infty,+\infty)$上的函数, 满足

$$\vert f(x)-f(y)\vert \le\vert x-y\vert^{\alpha},  \qquad \forall x,y\in(-\infty,+\infty).$$

其中实数$\alpha>1$. 
证明：对任意的$x,y\in(-\infty,+\infty)$以及任意的正整数$n$, 都有

$$\vert f(x)-f(y)\vert \le \dfrac{1}{n^{\alpha-1}}\vert x-y\vert^{\alpha}.$$

进而推导出$f(x)$必为常值函数.


{: .note }
> 下面的题可以用来巩固一下对“上确界”概念的理解.

**3.** 设$E$是数集, 函数$f:E\to\mathbb{R}$. 定义函数$f$的**连续模(modulus of continuity)**为

$$\omega(\delta)=\sup\{\vert f(x_1)-f(x_2)\vert \,\vert x_1,x_2\in E, \vert x_1-x_2\vert  < \delta\}$$

证明: 

(1)$\omega(\delta)$是单调不降的非负函数, 并且在$0$处存在右极限:

$$\omega(0^+)=\lim\limits_{\delta\to 0^+}\omega(\delta).$$

(2)对任意的$\varepsilon>0$, 存在$\delta > 0$, 使得对任意$x_1,x_2\in E$, 当$\vert x_1 - x_2 \vert < \delta$时, 有

$$\vert f(x_1)-f(x_2)\vert  < \omega(0^+) + \varepsilon.$$

(3)若$E$是区间(例如: 闭区间、开区间、半开半闭区间), 则

$$\omega(\delta_1+\delta_2) \le \omega(\delta_1) + \omega(\delta_2).$$

(4)设$E=\mathbb{R}$, 则函数$f(x)=x$的连续模为$\omega(\delta)=\delta(\forall \delta>0)$.

(5)设$E=\mathbb{R}$, 则函数$f(x)=\sin(x^2)$的连续模为$\omega(\delta)=2(\forall \delta>0)$.

(6)函数$f$在集合$E$上一致连续当且仅当$\omega(0^+)=0$. 


{% endraw %}
