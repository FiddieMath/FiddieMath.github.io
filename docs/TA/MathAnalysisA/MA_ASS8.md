---
layout: default
title: 第8次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 13
---

## 第8次作业

习题4.1/2, 4, 6, 10, 12(1)(3)(5), 13偶数题, 14奇数题, 15偶数题, 16奇数题, 18.

## 主要问题

还没改，别急

## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.** 设$f(x)$在$a$处可导, $n$是正整数. 计算极限

$$\lim\limits_{x\to a}\dfrac{a^nf(x)-x^nf(a)}{x-a}.$$

&nbsp; 

&nbsp; 

**2.** 设$f:\mathbb{R}\to\mathbb{R}$. 

(1)若$f$在$\mathbb{R}$上处处可微, 证明：$\lim\limits_{n\to\infty}n\left[f(x+\tfrac{1}{n})-f(x)\right]$存在并且等于$f'(x)$.

(2)举例说明上述命题的逆命题是假命题, 
即存在无处可微的函数$f$使得$\lim\limits_{n\to\infty}n\left[f(x+\tfrac{1}{n})-f(x)\right]$存在.

&nbsp; 

&nbsp; 

{: .note}
> 下面这题中, 符号$\lim\limits_{u\to x_0^-, v\to x_0^+}g(u,v)=A$指的是:
> 对任意$\varepsilon>0$, 存在$\delta>0$, 当$x_0-\delta < u < x_0 < v < x_0+\delta$时, 
> 有$\vert g(u,v)-A\vert  < \varepsilon$. 
>
> 符号$\lim\limits_{u\to x_0, v\to x_0, u\ne v}g(u,v)=A$指的是:
> 对任意$\varepsilon>0$, 存在$\delta>0$, 当$u,v\in V(x_0,\delta)$且$u\ne v$时, 
> 有$\vert g(u,v)-A\vert  < \varepsilon$. 


**3.** 设$f:\mathbb{R}\to\mathbb{R}$, $x_0\in\mathbb{R}$. 

(1)证明: $f$在$x_0$处可微的充分必要条件是: 极限

$$\lim\limits_{u\to x_0^-, v\to x_0^+}\dfrac{f(v)-f(u)}{v-u}$$

存在(且有限), 并且此时上述极限的值为$f'(x_0)$. 

{: .note}
> 称$f$在$x_0$处**强可微(strongly differentiable)**, 若极限
> 
> $$\lim\limits_{u\to x_0, v\to x_0, u\ne v}\dfrac{f(v)-f(u)}{v-u}$$
> 
> 存在(且有限). 

(2)举例说明可微函数不一定是强可微的. 

(3)证明强可微的函数一定是可微的.

(4)若$f$在$x_0$处强可微, 并且在$x_0$的邻域中可微, 则$f'$在$x_0$处连续.

&nbsp; 

&nbsp;
