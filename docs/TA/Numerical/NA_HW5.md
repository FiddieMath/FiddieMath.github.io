---
layout: default
title: 第5周作业+补充习题
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 5
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




# 第5周作业

林成森《数值计算方法》第4章习题37、40，以及下面的两道题：

**31．** 设函数 $f(x)$ 在 $[a,b]$ 上具有四阶连续导数，试构造三次多项式 $H_3(x)$，使其满足插值条件

$$H_3(a)=f(a), \quad H_3'(a)=f'(a), \quad H_3^{\prime\prime}(a)=f^{\prime\prime}(a), H_3^{\prime\prime}(b)=f^{\prime\prime}(b).$$

并求其余项 $f(x)-H_3(x)$ 的表达式．

**32．** 设函数 $f(x)$ 在 $[a,b]$ 上具有四阶连续导数，试构造三次多项式 $H_3(x)$，使其满足插值条件

$$H_3(a)=f(a), \quad H_3(b)=f(b), \quad H_3(c)=f(c), H_3'(c)=f'(c).$$

其中 $c=\dfrac{a+b}{2}$，并求其余项 $f(x)-H_3(x)$ 的表达式．

# 解析

## 讲义第31题

设 

$$H_3(x) = f(a) + f'(a)(x-a) + \dfrac{f^{\prime\prime}(a)}{2}(x-a)^2 + C(x-a)^3,$$

其中 $C$ 是待定系数，则 $H_3(x)$ 满足前三个插值条件，而

$$H_3^{\prime\prime}(x) = f^{\prime\prime}(a) + 6C(x-a),$$

代入 $x=b$ 结合第四个插值条件得 

$$C = \dfrac{f^{\prime\prime}(b)-f^{\prime\prime}(a)}{6(b-a)}.$$

这样便能得到 $H_3(x)$ 的表达式．

**【方法一】** 为求余项 $r(x) = f(x) - H_3(x)$，依据插值条件，可设 

$$r^{\prime\prime}(x) = K(x)(x-a)(x-b). \qquad (1)$$

设辅助函数为

$$F(t) = f^{\prime\prime}(t) - H_3^{\prime\prime}(t) - K(x)(t-a)(t-b),$$

仿照书上定理证明，用两次 Rolle 定理，得 $K(x) = \dfrac{f^{(4)}(\eta)}{2}$．对 $(1)$ 式积分两次，可得

$$r(x)=\int_a^x\mathrm{d}m\int_a^m\dfrac{f^{(4)}(\eta)}{2}(t-a)(t-b)\mathrm{d}t, \quad \eta\in[a,b]. \qquad (2)$$

用一下积分中值定理，把 $f^{(4)}(\eta)$ 项提到积分外面，上式变成

$$r(x)=\dfrac{f^{(4)}(\xi)}{2}\int_a^x\mathrm{d}m\int_a^m(t-a)(t-b)\mathrm{d}t, \quad \eta\in[a,b].$$

然后剩下的积分很容易算出结果为 

$$r(x)=\dfrac{(x-a)^3(x+a-2b)}{24}f^{(4)}(\xi).$$

**【方法二】** 令

$$K(x)=\dfrac{f(x)-H_3(x)}{(x-a)^3(x+a-2b)}, \qquad (3)$$

构造辅助函数

$$F(t)=f(t) - H_3(t) - K(x)(t-a)^3(t+a-2b), \qquad (4)$$

求导计算得

$$\begin{aligned}
F'(t)&=f'(t)-H_3'(t) - 2K(x)(t-a)^2(2t+a-3b), && (5) \\
F^{\prime\prime}(t)&=f^{\prime\prime}(t)-H_3^{\prime\prime}(t) - 12K(x)(t-a)(t-b). && (6)
\end{aligned}$$

由 $(3)(4)$ 式， $F(a)=F(x)=0$，依 Rolle 定理，存在 $\xi_1\in (a,x)$ 使得 $F'(\xi_1)=0$．

由 $(5)$ 式， $F'(a)=F'(\xi_1)=0$，依 Rolle 定理，存在 $\xi_2\in(a,\xi_1)$ 使得 $F^{\prime\prime}(\xi_2)=0$．

由 $(6)$ 式， $F^{\prime\prime}(a)=F^{\prime\prime}(\xi_2)=F^{\prime\prime}(b)=0$，依 Rolle 定理，存在 $\xi_3\in(a,\xi_2)$，$\xi_4\in(\xi_2,b)$，使得 $F^{(3)}(\xi_3)=F^{(4)}(\xi_4)=0$．

依 Rolle 定理，存在 $\xi\in(\xi_3,\xi_4)$，使得$F^{(4)}(\xi)=0$．求导计算得

$$F^{(4)}(t) = f^{(4)}(t) - H_3^{(4)}(t) - 24 K(x),$$

因为 $H_3^{(4)}(t)=0$，所以 $K(x) = \dfrac{f^{(4)}(\xi)}{24}$．最后，再结合 $(3)$ 可得

$$r(x)=\dfrac{(x-a)^3(x+a-2b)}{24}f^{(4)}(\xi).$$

**【方法三】** 如果不能想到余项表达式为

$$r(x) = K(x)(x-a)^3(x+a-2b),$$

也可以采用待定系数的方法，设

$$r(x) = K(x)(x-a)^3(x-s),$$

其中 $s$ 是待定系数，使得 $r(a)=r'(a)=r^{\prime\prime}(a)=r^{\prime\prime}(b)=0$．在后续用 Rolle 定理求解过程中，根据 $r^{\prime\prime}(b)=0$ 可解出 $s=2b-a$．

### 错解

**【错解1】** 得到 $(2)$ 之后就戛然而止．

**【错解2】** 计算出错，系数少了一个常数倍．

**【错解3】** 没按要求给出余项表达式，而是估计了余项的上界．不仅如此，估计时还漏绝对值．

**【错解4】** 直接说可设

$$r(x)=K(x)(x-a)^3(x+a-2b)$$

并辅助函数为

$$F(t) = f(t) - H_3(t) - K(x)(t-a)^3(t+a-2b),$$

然后就没有写 $(3)$ 式，直接断言 $F(x)=0$．为什么可这样设 $r(x)$ ？需写清楚现有哪个函数然后有哪个函数的问题．

应像方法二那样，先按 $(3)$ 式设 $K(x)$，最后得到 $K(x) = \dfrac{f^{(4)}(\xi)}{24}$，然后通分变形，最终得到

$$r(x) = f(x) - H_3(x) = K(x)(x-a)^3(x+a-2b).$$


**【错解5】** 用了3次Rolle定理，得到了奇怪的结果（包含了 $f$ 的三次导数），比如

$$K(x)=\dfrac{1}{6}\left[f^{(3)}(\xi) - \dfrac{f^{\prime\prime}(a)-f^{\prime\prime}(b)}{a-b}\right]$$


**【错解6】** 没有构造辅助函数然后用 Rolle 定理，设 $r(x) = f(x) - H_3(x)$，由题目条件可知 $r^{\prime\prime}(x)$ 至少有 2 个零点 $a$，$b$，假设

$$r^{\prime\prime}(x)=K(x-a)(x-b),$$

那么取不定积分可得

$$r'(x) = \dfrac{1}{2}K(x-a)^2(x-b) -\dfrac{1}{6}K(x-a)^3,$$

进一步

$$r(x) = \dfrac{1}{6}K(x-a)^3(x-b) -\dfrac{1}{24}K(x-a)^4.$$

**错因：** 从 $r^{\prime\prime}(x)$ 到 $r'(x)$ 取不定积分这一步是错的，因为 $K$ 不是常数，而是与 $x$ 有关的函数．


**【错解7】** 不同的同学构造了各种不同的辅助函数，比如

$$\begin{gathered}
F(t) = f(t) - H_3(t) - K(x)(t-a)^3(t-b), \\
F(t) = f(t) - H_3(t) - K(x)(t-a)^2(t-b)^2,
\end{gathered}$$

然后断言 $F(a)=F(x)=0$．为什么能说 $F(x)=0$ ？

**【错解8】** 设 $r(x) = K(x)(x-a)^3(x-b)^3$，构造辅助函数

$$F(t) = f(t) - H_3(t) - K(x)(t-a)^3(t-b)^3.$$

这样设 $r(x)$ 的后果是强行加入了题目没有的条件 $f(b)=H_3(b)$ 和 $f'(b) = H_3'(b)$，得到的余项是不对的．

## 讲义第32题

**【方法一】** 设

$$H_3(x) = f(c) + f'(c)(x-c) + (Ax+B)(x-c)^2,$$

其中 $A$，$B$是待定系数，则 $H_3(x)$ 满足最后两个插值条件．由前两个插值条件，得

$$\left\{\begin{aligned}
f(a) &= f(c) + f'(c)(a-c) + (Aa+B)(a-c)^2, \\
f(b) &= f(c) + f'(c)(b-c) + (Ab+B)(b-c)^2, \\
\end{aligned}\right.$$

看作关于 $A$，$B$ 的线性方程组，可解出 $A$，$B$．

**【方法二】** 设

$$H_3(x) = N_2(x) + A(x-x_0)(x-x_1)(x-x_2),$$

其中 $A$ 是待定系数，则 $H_3(x)$ 满足前三个插值条件．由最后一个插值条件，将 $A$ 解出来即可．

为了求余项，仿照书上第 4.5 节的推导方法，反复用 Rolle 定理即可．

## 教材第37题

思路类似于讲义第32题．最终得到的余项是

$$f(x)-H_3(x) = \dfrac{(x-x_0)(x-x_1)^2(x-x_2)}{4!}f^{(4)}(\xi)$$

其中 $\xi$ 介于 $x_0$ 与 $x_2$．

## 教材第40题

得到

$$S_C(x)=\left\{\begin{aligned}
&1+(x-1)+\dfrac{11}{7}(x-1)^2-\dfrac{4}{7}(x-1)^3, &&x\in[1,2], \\
&3+\dfrac{17}{7}(x-2)-\dfrac{1}{7}(x-2)^2 - \dfrac{2}{7}(x-2)^3, &&x\in[2,4], \\
&5-\dfrac{11}{7}(x-4)-\dfrac{13}{7}(x-4)^2+\dfrac{3}{7}(x-4)^2, &&x\in[4,5].
\end{aligned}\right.$$

估计值为：$f(1.5)\approx \dfrac{51}{28}$，$f(3)\approx 5$．


# 第4周答疑

## 补充习题（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1．** 证明：具有结点 $t_0 < t_1 < \cdots < t_n$ 的一次样条函数可表示为

$$S(x)=ax+b+\sum\limits_{i=1}^{n-1}c_i|x-t_i|.$$

**2．** 在计算机中实现用三次样条函数来刻画平面或空间中的参数曲线．可参考[这个链接](/docs/TA/Numerical/Interp_Spline_App/)．


