---
layout: default
title: 第6周作业 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 6
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

# 第 6 周作业（理论6）

讲义第二章26、27、28，第三章2、4、6

# 解答

### 第26题解答

{: .problem}
> 已知函数 $y=f(x)$ 在若干点的函数值：
>
> $f(1)=1$, $f(2)=3$, $f(4)=4$, $f(5)=2$，
>
> 且 $f^{\prime\prime}(1)=f^{\prime\prime}(5)=0$．试求 $f(x)$ 的自然三次样条插值函数 $S_N(x)$，并求 $f(3)$ 的近似值．

答案：

$$S_N(x)=\left\lbrace\begin{aligned}
&-\frac{1}{8}(x-1)^3+\frac{17}{8}(x-1)+1, && x\in[1,2], \\
&-\frac{1}{8}(x-2)^3-\frac{3}{8}(x-2)^2+\frac{7}{4}(x-2)+3, && x\in[2,4], \\
&\frac{3}{8}(x-4)^3-\frac{9}{8}(x-4)^2-\frac{5}{4}(x-4)+4, && x\in[4,5].
\end{aligned}\right.$$

其中，$f(3)\approx S_N(3)=\dfrac{17}{4}$．

### 第27题解答

{: .problem}
> 已知 $f(x)$ 在若干点的取值：
> 
> $f(1)=1$，$f(2)=3$，$f(4)=5$，$f(5)=2$，$f'(1)=1$，$f'(5)=-4$．
>
> 求完备三次样条插值函数 $S_C(x)$，并计算 $f(1.5)$ 和 $f(3)$ 的近似值．

答案：

$$S_C(x)=\left\lbrace\begin{aligned}
&-\frac{4}{7}(x-1)^3+\frac{11}{7}(x-1)^2+(x-1)+1, && x\in[1,2], \\
&-\frac{2}{7}(x-2)^3-\frac{1}{7}(x-2)^2 +\frac{17}{7}(x-2)+3, && x\in[2,4], \\
& \frac{3}{7}(x-4)^3-\frac{13}{7}(x-4)^2-\frac{11}{7}(x-4)+5, && x\in[4,5].
\end{aligned}\right.$$

其中，$f(1.5)\approx S_C(1.5)=\dfrac{51}{28}$，$f(3)\approx S_C(3)=5$．

### 第28题解答

{: .problem}
> 函数 $f(x)$ 在 $[a,b]$ 上一次连续可微，给定节点组 $a=x_1 < x_2 < \cdots < x_{n+1}=b$，及节点处的函数值：$f(x_j)=f_j$，$j=1,\cdots,n+1$．设函数
>
> $$S(x)=\left\lbrace\begin{aligned}
&S_1(x), && x\in[x_1,x_2], \\
&\cdots, &&\cdots \\
&S_i(x), &&x\in[x_{i},x_{i+1}], \\
&\cdots, &&\cdots \\
&S_n(x), && x\in[x_n,x_{n+1}].
\end{aligned}\right.$$
>
> 一次连续可微，且 $S_i(x)$, $i=1,2,\cdots,n$ 是不高于二次的多项式，满足
>
> $S(x_j)=f_j$，$j=1,\cdots,n+1$．
>
> 则称 $S(x)$ 为函数 $f(x)$ 的“二次样条插值函数”．试给出一种边界条件下的 $S(x)$ 的计算方法，注意设计的算法应采用尽可能少的未知量（如以节点处的导数为未知量）．

可以从自由度的角度来思考这个问题．每个二次函数都由三个系数确定，即总共有 $3n$ 个待定系数．

①插值条件 

$$S(x_j)=f_j, \qquad j=1,\cdots,n+1,$$

共有 $n+1$ 个方程．

②在节点 $x_2,x_3,\cdots,x_n$ 处可以添加 $C^1$ 条件，即

$$S_i(x_{i+1})=S_{i+1}(x_{i+1}), \qquad S_i'(x_{i+1})=S_{i+1}'(x_{i+1}).$$

这里共有 $2(n-1)$ 个方程．

于是，上面一共有 $3n-1$ 个方程，只需再添加一个方程即可．

首先整理一下上面的方程．注意，$S'$ 是分段线性函数，记

$$\alpha_i=S'(x_i), \qquad i=1,\cdots,n+1,$$

则

$$S_i'(x)=\alpha_i\dfrac{x_{i+1}-x}{x_{i+1}-x_i}+\alpha_{i+1}\dfrac{x-x_i}{x_{i+1}-x_i}, \quad x\in[x_i,x_{i+1}],$$

求不定积分得

$$S_i(x)=-\alpha_i\dfrac{(x_{i+1}-x)^2}{2(x_{i+1}-x_i)}+\alpha_{i+1}\dfrac{(x-x_i)^2}{2(x_{i+1}-x_i)}+C_i,\quad x\in[x_i,x_{i+1}].$$

因为当 $i=1,\cdots,n$ 时， $S_i(x_i)=f_i$，$S_i(x_{i+1})=f_{i+1}$，所以

$$\begin{aligned}
&f_i=-\dfrac{\alpha_i(x_{i+1}-x_i)}{2}+C_i, \\
&f_{i+1}=\dfrac{\alpha_{i+1}(x_{i+1}-x_i)}{2}+C_i,
\end{aligned}$$

两式相减可得

$$f_{i+1}-f_i=(\alpha_{i+1}+\alpha_i)\cdot\dfrac{x_{i+1}-x_i}{2}.$$

即 $\alpha_{i+1}=\alpha_i-2f[x_i,x_{i+1}]$，$i=1,\cdots,n$．

注意 $\alpha_1=f'(x_1)$ 并不在①②中，所以可以考虑添加这个条件（当然，添加其它条件也可以，下面就以这个条件为例来写算法）．

将 $S_i(x)$ 改写为

$$S_i(x)=C_{i,0}+C_{i,1}(x-x_i)+C_{i,2}(x-x_i)^2,\quad x\in[x_i,x_{i+1}],$$

可得 $C_{i,0}=f_i$，$C_{i,1}=\alpha_i$，$C_{i,2}=\dfrac{\alpha_{i+1}-\alpha_i}{2(x_{i+1}-x_i)}=\dfrac{1}{2}\alpha[x_i,x_{i+1}]$．

最终，函数值 $S(x)$ 的各个系数的计算步骤如下：

- Step 1：$\alpha_1=f'(x_1)$．
- Step 2：对 $i=1,\cdots,n$，
- - 计算 $\alpha_{i+1}=\alpha_i-2f[x_i,x_{i+1}]$．
- - $C_{i,0}=f(x_i)$，
- - $C_{i,1}=\alpha_i$，
- - $C_{i,2}=\dfrac{1}{2}\alpha[x_i,x_{i+1}]$．

### 第2题解答

{: .problem}
> 设函数 $f(x)$ 在区间 $[a,b]$ 上连续，试证明 $f(x)$ 的 $n$ 次最佳一致逼近多项式是 $f(x)$ 在 $[a,b]$ 上的某一个 Lagrange 插值多项式．

设 $p(x)$ 是 $f(x)$ 的最佳一致逼近多项式．由 Chebyshev 定理，$f(x) - p(x)$ 在 $[a,b]$ 上存在一个至少由 $n+2$ 个点组成的交错点组，记为 $x_0 < x_1 < \cdots < x_{n+1}$．于是

$$p(x_i) = f(x_i) + (-1)^i\sigma\cdot E_n,$$

其中$\sigma\in\lbrace\pm 1\rbrace$，$i=0,1,\cdots,n+1$，且

$$E_n=\min\limits_{p_n(x)\in H_n}\max\limits_{a\le x\le b}\vert f(x)-p_n(x)\vert.$$

依介值定理，在 $[a,b]$ 上至少存在 $n+1$ 个点 $\eta_0,\cdots,\eta_n$，使得

$$p(\eta_i)=f(\eta_i), \quad i=0,1,\cdots,n.$$

又因为 $p(x)\in H_n$，根据 Lagrange 插值多项式的唯一性可知， $p(x)$ 是 $f(x)$ 在插值点 $\eta_0,\cdots,\eta_n$ 处的插值多项式．


### 第4题解答

{: .problem}
> 记 $H_2 = \mathrm{span}\lbrace 1,x,x^2\rbrace$ 是二次多项式空间．求 $p(x) \in H_2$ 使得 
>
> $$\max\limits_{x\in[0,2]} \vert x^3-p(x)\vert$$
>
> 达到最小．

书上似乎没强调用 $H_{n-1}$ 中多项式逼近 $H_n$ 中多项式的特殊情况．这里作一个补充说明．

下面考虑区间 $[-1,1]$ 上的函数的最佳一致逼近．我们有如下定理，其实类似于补充讲义第12页的(3.3.13)式，即 Chebyshev 多项式的性质(9)：

{: .theorem}
> **首一多项式定理：** 若 $p(x)$ 是 $n$ 次首一多项式，则
>
> $$\Vert p\Vert_{\infty}\triangleq \max\limits_{-1\leq x\leq 1}\vert p(x)\vert \geq 2^{1-n}.$$
>
> 等号成立条件是 $p(x) = \dfrac{T_n(x)}{2^{n-1}}$．

**证明：** (反证)设

$$\vert p(x)\vert< 2^{1-n}, |x|\leq 1.$$

令 $q(x)=2^{1-n}T_n(x)$，$x_j=\cos\dfrac{j\pi}{n}$． 

由于 $q(x)$ 首一，则

$$(-1)^jp(x_j)\leq \vert p(x_j)\vert < 2^{1-n}=(-1)^jq(x_j),$$

则

$$(-1)^j[q(x_j)-p(x_j)]>0, 0\leq i\leq n.$$

所以在区间 $[-1,1]$ 上，多项式 $q(x)-p(x)$ 的符号在正负之间变动$n+1$次．从而由介值定理可知在区间 $(-1,1)$ 内 $q(x)-p(x)$ 至少有$n$个根，但这是不可能的，因为 $q(x)-p(x)$ 次数至多是 $n-1$ （注意$p(x)$，$q(x)$都是首一 $n$ 次多项式，故 $q(x)-p(x)$不会出现$x^n$）．

特别地，当 $p(x) = \dfrac{T_n(x)}{2^{n-1}}$ 时，等号成立．$\square$

{: .remark}
> 上述定理表明，使得 $\Vert p(x)\Vert_{C[-1,1]}$ 最小的  $n$ 次首一多项式 $p(x)$ 是 $n$ 次首一 Chebyshev 多项式 $\dfrac{T_n(x)}{2^{n-1}}$．

根据这个定理，如果我们要找 $q(x)\in H_{n-1}[-1,1]$ 来逼近 $f(x)\in H_n[-1,1]$，使得 $\Vert f(x)-q(x)\Vert_{\infty}$ 最小的那个 $q(x)$ 满足

$$\dfrac{f(x)-q(x)}{a_n}=\dfrac{T_n(x)}{2^{n-1}},$$

即

$$\boxed{q(x)=f(x)-\dfrac{a_n}{2^{n-1}}T_n(x).}$$

其中 $a_n$ 代表 $f(x)$ 的最高次项系数．

一般地，若 $f(x)$ 定义在 $[a,b]$ 上，先把 $f(x)$ 作个平移伸缩变成 $[-1,1]$．

{: .remark}
> **注：** Chebyshev多项式递推关系式是 $T_{n+1}(x)=2xT_n(x)-T_{n-1}(x)$．可以表示成 $T_n(x)=\cos(n\arccos x)$．前几个Chebyshev多项式是
> 
> $$\begin{aligned}
        T_0(x)&=1 \\
        T_1(x)&=x \\
        T_2(x)&=2x^2-1 \\
        T_3(x)&=4x^3-3x \\
        T_4(x)&=8x^4-8x^2+1
    \end{aligned}$$

所以第4题解决方法如下：

**Step 1：平移．** 设 $g(x)=f(x+1)=(x+1)^3$，$x\in[-1,1]$．

**Step 2：求 $g(x)$ 的最佳一致逼近多项式．** 根据前面的理论，知 $p(x)$ 的最佳一致逼近多项式为

$$\begin{aligned}
h(x) &= g(x) - \dfrac{1}{2^2}T_3(x) \\
&= (x+1)^3 - (x^3-\dfrac{3}{4}x).
\end{aligned}$$

**Step 3：平移得到 $f(x)$ 的最佳一致逼近多项式．** $f(x)$ 的最佳一致逼近多项式是

$$\begin{aligned}
p(x) &= h(x-1) \\
&= x^3 - (x-1)^3 + \dfrac{3}{4}(x-1) \\
&= \boxed{3x^2-\dfrac{9}{4}x+\dfrac{1}{4}}.
\end{aligned}$$

### 第6题解答

{: .problem}
> 设 $f(x)$ 在区间 $[a,b]$ 上连续，试证 $f(x)$ 的零次最佳一致逼近多项式是
> 
> $$p(x)=\dfrac{M+m}{2},$$
> 
> 其中 
> 
> $$M=\max\limits_{a\le x\le b}f(x), \quad m=\min\limits_{a\le x\le b}f(x).$$

本题验证定义．零次最佳一致逼近多项式 $p_0(x)=c$ 使得

$$\max\limits_{x\in[a,b]}\vert f(x)-p_0(x)\vert$$ 

达到最小．而 

$$\max\limits_{x\in[a,b]}\vert f(x)-c\vert = \max\lbrace M-c,c-m\rbrace \ge \dfrac{(M-c)+(c-m)}{2},$$

等号成立条件是 $c = \boxed{\dfrac{M+m}{2}}$．所以当 $c=\dfrac{M+m}{2}$ 时，$p_0(x)=c$ 是最佳一致逼近多项式．

















