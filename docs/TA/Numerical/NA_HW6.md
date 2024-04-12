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

## 第6周作业

{: .note}
> 本次布置的作业，书上笔误较多．

讲义第三章习题2，4，5，6，7，8，9，12

**2．** 设函数 $f(x)$ 在区间 $[a,b]$ 上连续，试证明 $f(x)$ 的 $n$ 次最佳一致逼近多项式是 $f(x)$ 在 $[a,b]$ 上的某一个 Lagrange 插值多项式．

**4．** 记 $H_2 = \mathrm{span}\lbrace 1,x,x^2\rbrace$ 是二次多项式空间．求 $p(x) \in H_2$ 使得 

$$\max\limits_{x\in[0,2]} \vert x^3-p(x)\vert$$

达到最小．

**5．** 求 $f(x) = \dfrac{1}{1+x}$ 在 $[0,1]$ 上的一次最佳一致逼近多项式．

**6．** 设 $f(x)$ 在区间 $[a,b]$ 上连续，试证 $f(x)$ 的零次最佳一致逼近多项式是

$$p(x)=\dfrac{M+m}{2},$$

其中 

$$M=\max\limits_{a\le x\le b}f(x), \quad m=\min\limits_{a\le x\le b}f(x).$$

**7．** 对下列给定的权函数 $W(x)$，求出区间 $[-1,1]$ 上的直交多项式系的前三个多项式 $p_0(x)$、$p_1(x)$、$p_2(x)$．

(1) $W(x)=\dfrac{1}{\sqrt{1+x^2}}$，

(2) $W(x)=1+x^2$．

**8．** 设 $q_n(x)$ 是区间 $[a,b]$ 上关于权函数 $W(x)$ 的首一 $n$ 次直交多项式，令

$$A_n=\begin{bmatrix}
\alpha_0 & \sqrt{\beta_1} \\
\sqrt{\beta_1} & \alpha_1 \\
&\ddots&\ddots&\ddots \\
&&&\alpha_{n-2}&\sqrt{\beta_{n-1}} \\
&&&\sqrt{\beta_{n-1}} & \alpha_{n-1}
\end{bmatrix}, n\ge 1.$$

其中 $\alpha_k$、$\beta_k$ 为递推关系式 (3.3.4) 中的系数．试证，矩阵 $A_n$ 的特征值是直交多项式 $q_n(x)$ 的根．

**9．** 设

$$X_n(x,y)=T_{n+1}(x)T_n(y)-T_{n+1}(y)T_n(x),$$

其中 $T_n$ 表示 Chebyshev 多项式，证明

$$X_n(x,y)=2(x-y)T_n(x)T_n(y)+X_{n-1}(x,y), \quad n\ge 1.$$

并导出

$$\dfrac{1}{2}X_n(x,y)=(x-y)\left[
\sum\limits_{k=1}^nT_k(x)T_k(y)\right].$$

**12．** 设 $p_n(x)$ 为不高于 $n$ 次的多项式，令

$$M=\max\limits_{-1\le x\le 1}\vert p_n(x)\vert$$

试证明对任何大于 1 的实数 $y$，恒有

$$\vert p_n(y)\vert \le M\vert T_n(y)\vert .$$

## 解答

### 第2题

设 $p(x)$ 是 $f(x)$ 的最佳一致逼近多项式．由 Chebyshev 定理，$f(x) - p(x)$ 在 $[a,b]$ 上存在一个至少由 $n+2$ 个点组成的交错点组，记为 $x_0 < x_1 < \cdots < x_{n+1}$．于是

$$p(x_i) = f(x_i) + (-1)^i\sigma\cdot E_n,$$

其中$\sigma\in\{\pm 1\}$，$i=0,1,\cdots,n+1$，且

$$E_n=\min\limits_{p_n(x)\in H_n}\max\limits_{a\le x\le b}\vert f(x)-p_n(x)\vert.$$

依介值定理，在 $[a,b]$ 上至少存在 $n+1$ 个点 $\eta_0,\cdots,\eta_n$，使得

$$p(\eta_i)=f(\eta_i), \quad i=0,1,\cdots,n.$$

又因为 $p(x)\in H_n$，根据 Lagrange 插值多项式的唯一性可知， $p(x)$ 是 $f(x)$ 在插值点 $\eta_0,\cdots,\eta_n$ 处的插值多项式．

### 第4题

书上似乎没讲用 $H_{n-1}$ 中多项式逼近 $H_n$ 中多项式的特殊情况．这里作一个补充：

考虑区间 $[-1,1]$ 上的函数的最佳一致逼近．我们有如下定理：

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

### 第5题

可以用 Chebyshev 定理．设 $p(x)=ax+b$ 是 $f(x)$ 的最佳一致逼近多项式，则 $g(x)=f(x)-p(x)$ 有由 3 个点构成的交错点组．

另一方面，$g(x) = \dfrac{1}{1+x}+ax+b$，$g'(x) = -\dfrac{1}{(1+x)^2}+a$，$g^{\prime\prime}(x)=\dfrac{2}{(1+x)^3} > 0$ 于 $[0,1]$ 成立，所以 0 和 1 属于交错点组．因此可设交错点组中余下的点为 $c$，则 $c$ 是极值点，故

$$\left\{\begin{aligned}
& g'(c)=0, \\
& g(0)=-g(c)=g(1)=E_1.
\end{aligned}\right.$$

即 

$$\left\{\begin{aligned}
& -\dfrac{1}{(1+c)^2}+a=0, \\
& 1+b = E_1, \\
& -\dfrac{1}{1+c}+ac+b = E_1, \\
& \dfrac{1}{2}+a+b = E_1.
\end{aligned}\right.$$

这里有 4 个未知数和 4 个方程，最终可以解得

$$a=-\dfrac{1}{2}, \quad b=\dfrac{1}{4}+\dfrac{\sqrt{2}}{2}.$$

故一次最佳一致逼近多项式是

$$p(x) = \boxed{-\dfrac{1}{2}x+\dfrac{1}{4}+\dfrac{\sqrt{2}}{2}}.$$

### 第6题

本题验证定义．零次最佳一致逼近多项式 $p_0(x)=c$ 使得

$$\max\limits_{x\in[a,b]}\vert f(x)-p_0(x)\vert$$ 

达到最小．而 

$$\max\limits_{x\in[a,b]}\vert f(x)-c\vert = \max\lbrace M-c,c-m\rbrace \ge \dfrac{(M-c)+(c-m)}{2},$$

等号成立条件是 $c = \boxed{\dfrac{M+m}{2}}$．所以当 $c=\dfrac{M+m}{2}$ 时，$p_0(x)=c$ 是最佳一致逼近多项式．

### 第7题

回顾：直交多项式可由以下方法递推得到．

{: .theorem}
> **直交多项式定理**：在由全体一元多项式组成的实内积空间 $H$ 中，如下归纳定义的多项式序列是直交的：
>
> $$p_n(x)=(x-a_n)p_{n-1}(x)-b_np_{n-2}(x),n\geq 2,$$
>
> 其中，
>
> $$p_0(x)=1, \quad p_1(x)=x-a_1,$$
>
> 并且
>
> $$\begin{aligned}
 a_n=\dfrac{(xp_{n-1},p_{n-1})}{(p_{n-1},p_{n-1})},
 b_n=\dfrac{(xp_{n-1},p_{n-2})}{(p_{n-2},p_{n-2})},
\end{aligned}$$
>
> 这里 $(p,q)$ 表示 $H$ 中的内积．比如可定义 $\displaystyle (p,q)=\int_0^1p(x)q(x)W(x)\mathrm{d}x$．

证明方法是待定系数法，即对

$$p_n(x)=(x-a_n)p_{n-1}(x)-b_np_{n-2}(x)$$

两边分别与 $p_{n-1}$ 和 $p_{n-2}$ 作内积得到两个等式，可解出 $a_n$ 与 $b_n$．另一方面，可以证明：当 $n\ge 2$ 时，

$$(xp_{n-1},p_{n-2}) = (p_{n-1},xp_{n-2}) = (p_{n-1},p_{n-1}).$$

所以也可以改写

$$ b_n=\dfrac{(p_{n-1},p_{n-1})}{(p_{n-2},p_{n-2})}.$$

第7题解答如下：

（1）解： $p_0(x)=\boxed{1}$，

因为 $\displaystyle (xp_0,p_0)=\int_{-1}^1xp_0(x)p_0(x)\dfrac{1}{\sqrt{1+x^2}}\mathrm{d}x=0$．

所以 $a_1=0$，$p_1(x)=\boxed{x}$．

因为 $\displaystyle (xp_1,p_1)=\int_{-1}^1xp_1(x)p_1(x)\dfrac{1}{\sqrt{1+x^2}}\mathrm{d}x=0$．

所以 $a_2=0$．

$\displaystyle (xp_1,p_0)=\int_{-1}^1xp_1(x)p_0(x)\dfrac{1}{\sqrt{1+x^2}}\mathrm{d}x=\sqrt{2}-\ln(1+\sqrt{2})$．

$\displaystyle (p_0,p_0)=\int_{-1}^1p_0(x)p_0(x)\dfrac{1}{\sqrt{1+x^2}}\mathrm{d}x=2\ln(1+\sqrt{2})$．

所以 $b_2 = \dfrac{\sqrt{2}-\ln(1+\sqrt{2})}{2\ln(1+\sqrt{2})}.$

所以 $p_2(x)=(x-a_2)p_1(x)-b_2p_0(x)=\boxed{x^2-\dfrac{\sqrt{2}-\ln(1+\sqrt{2})}{2\ln(1+\sqrt{2})}}.$

（2）$p_0(x)=\boxed{1}$，

因为 $\displaystyle (xp_0,p_0)=\int_{-1}^1xp_0(x)p_0(x)(1+x^2)\mathrm{d}x=0$．

所以 $a_1=0$，$p_1(x)=\boxed{x}$．

因为 $\displaystyle (xp_1,p_1)=\int_{-1}^1xp_1(x)p_1(x)(1+x^2)\mathrm{d}x=0$．

所以 $a_2=0$．

$\displaystyle (xp_1,p_0)=\int_{-1}^1xp_1(x)p_0(x)(1+x^2)\mathrm{d}x=\dfrac{16}{15}$．

$\displaystyle (p_0,p_0)=\int_{-1}^1p_0(x)p_0(x)(1+x^2)\mathrm{d}x=\dfrac{8}{3}$．

所以 $b_2 = \dfrac{2}{5}.$

所以 $p_2(x)=(x-a_2)p_1(x)-b_2p_0(x)=\boxed{x^2-\dfrac{2}{5}}.$



### 第8题

求特征多项式 $p_n(x)=\mathrm{det}(x I_n-A_n)$ 的递推关系式，发现它和直交多项式 $q_n(x)$ 的递推关系式完全一致．

又因为 $p_0(x)=q_0(x)$，$p_1(x)=q_1(x)$，依据递推式，可得 $p_k(x)=q_k(x)$ 对任意自然数 $k$ 成立．所以 $A_n$ 的特征值就是 $p_n(x)$ 的根，也是 $q_n(x)$ 的根．

### 第9题

依据 $T_n(x)$ 的递推式

$$T_{n+1}=2T_n(x)-T_{n-1}(x)$$

可以证明第一条式子．第二条式子采用裂项相消求和法．本题没什么难度．

### 第12题

{: .warning}
> 本题容易出现伪证．根据提交情况，同学们的证明方法五花八门，但很多都不正确，又或者仿照书中性质(9)想当然地“造”了一个性质，把最难证的部分一笔带过．
>
> 助教精力有限，无法一一展示于此，实在抱歉．如果同学们不太确定自己的证明是否正确，可联系助教．

设 $x_k=\cos\dfrac{\pi k}{n}$，$k=0,1,\cdots,n$．

注意到：$p_n(x)$ 在插值基点 $\lbrace(x_k,p_n(x_k))\rbrace_{k=0}^n$ 处的 Lagrange 插值多项式是 $p_n(x)$ 本身，所以

$$\begin{aligned}
p_n(x)&=\sum\limits_{k=0}^np_n(x_k)\prod\limits_{j\ne k}\dfrac{x-x_j}{x_k-x_j}.
\end{aligned}$$

所以，当 $y > 1$ 时，$y > x_j (j=0,1,\cdots,n)$，故

$$\begin{aligned}
\vert p_n(y)\vert 
&=\left\vert\sum\limits_{k=0}^n p_n(x_k)\prod\limits_{j\ne k}\dfrac{y-x_j}{x_k-x_j}\right\vert \\
&\le \sum\limits_{k=0}^n \vert p_n(x_k)\vert \prod\limits_{j\ne k}\dfrac{y-x_j}{\vert x_k-x_j\vert } \\
&\le M\sum\limits_{k=0}^n  \prod\limits_{j\ne k}\dfrac{y-x_j}{\vert x_k-x_j\vert }.
\end{aligned}$$

注意到，当 $k$ 为奇数时 $\prod\limits_{j\ne k}(x_k-x_j)$ 的符号与当 $k$ 为偶数时 $\prod\limits_{j\ne k}(x_k-x_j)$ 的符号相反，所以可以写

$$\prod\limits_{j\ne k}(x_k-x_j) = (-1)^k\sigma,$$

其中 $\sigma\in\lbrace \pm 1\rbrace$．

再注意到，Chebyshev 多项式在 $x_k$ 处的值 $T_n(x_k)=(-1)^k$．

因此，$\sum\limits_{k=0}^n (-1)^k\prod\limits_{j\ne k}\dfrac{y-x_j}{ x_k-x_j }$ 就是 $T_n(x)$ 插值基点为 $\lbrace (x_k,T_n(x_k))\rbrace_{k=0}^n$ 的 Lagrange 插值多项式．从而

$$\begin{aligned}
\vert p_n(y)\vert 
&\le M\sigma \sum\limits_{k=0}^n (-1)^k\prod\limits_{j\ne k}\dfrac{y-x_j}{ x_k-x_j } \\
&= M\sigma T_n(x) \\
&\le M \vert T_n(x)\vert.
\end{aligned}$$

证明完成．$\square$

你学会了吗？

