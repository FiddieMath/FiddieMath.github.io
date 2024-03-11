---
layout: default
title: 第2周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 2
---

## 第2周作业

新版讲义第一章1、4、8(3)、10(3)、13．

**1．** 应用梯形公式

$$T=\dfrac{b-a}{2}(f(a)+f(b))$$

计算积分

$$I=\int_0^1\mathrm{e}^{-x}\mathrm{d}x$$

的近似值，在整个计算过程中按四舍五入规则取五位小数．计算中产生的误差的主要原因是离散或是舍入？为什么？

**4．** 证明：若近似数$\overline{a}=\pm a_0a_1\cdots a_m.a_{m+1}\cdots a_n$的相对误差有估计式
$$\left|\dfrac{a-\overline{a}}{\overline{a}}\right| \le \dfrac{1}{2(a_s+1)}\times 10^{-(n-s)},$$
其中$a_s\ne 0$是$\overline{a}$的第一位有效数字，则$\overline{a}$至少具有$n+1-s$位有效数字．

**8(3)．** 当$x(>0)$很大时，如何计算$\dfrac{\sin x}{x-\sqrt{x^-1}}$，可使其误差较小？

**10(3)．** 在$p=10$，$t=4$，$L=U=5$的舍入（或断位）的假想计算机上，将下列实数写成相应的规格化浮点数：$52\dfrac{1}{3}$．

**13．** 设字长$t=8$，以及

$$\begin{aligned}
x&=0.23371258\times 10^{-4}, \\
y&=0.33678429\times 10^2, \\
z&=-0.33677811\times 10^2.
\end{aligned}$$

求：$fl(fl(x+y)+z)$，$fl(x+fl(y+z))$ 和 $x+y+z$．

## 解答

### 第4题解答

讨论$s=0$或$s\ne 0$，验证有效数字的定义即可．

思考：这题能不能说$\overline{a}$恰好有$n+1-s$位有效数字？








