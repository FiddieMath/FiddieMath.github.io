---
layout: default
title: 第7周作业 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 7
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

# 第 7 周作业（理论7）

第三章7、8、9、13、16、18(2)、21

# 解答

### 第7题解答

{: .problem}
>  对下列给定的权函数 $W(x)$，求出区间 $[-1,1]$ 上的直交多项式系的前三个多项式 $p_0(x)$、$p_1(x)$、$p_2(x)$．
> 
> (1) $W(x)=\dfrac{1}{\sqrt{1+x^2}}$，
> 
> (2) $W(x)=1+x^2$．

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




### 第8题解答

{: .problem}
>  设 $q_n(x)$ 是区间 $[a,b]$ 上关于权函数 $W(x)$ 的首一 $n$ 次直交多项式，令
> 
> $$A_n=\begin{bmatrix}
\alpha_0 & \sqrt{\beta_1} \\
\sqrt{\beta_1} & \alpha_1 \\
&\ddots&\ddots&\ddots \\
&&&\alpha_{n-2}&\sqrt{\beta_{n-1}} \\
&&&\sqrt{\beta_{n-1}} & \alpha_{n-1}
\end{bmatrix}, n\ge 1.$$
> 
> 其中 $\alpha_k$、$\beta_k$ 为递推关系式 (3.3.3) 中的系数：
> 
> $$p_{k+1}=(x-\alpha_k)p_k(x)-\beta_kp_{k-1}(x).$$
> 
> 试证，矩阵 $A_n$ 的特征值是直交多项式 $q_n(x)$ 的根．

求特征多项式 $p_n(x)=\mathrm{det}(x I_n-A_n)$ 的递推关系式，发现它和直交多项式 $q_n(x)$ 的递推关系式完全一致．

又因为 $p_0(x)=q_0(x)$，$p_1(x)=q_1(x)$，依据递推式，可得 $p_k(x)=q_k(x)$ 对任意自然数 $k$ 成立．所以 $A_n$ 的特征值就是 $p_n(x)$ 的根，也是 $q_n(x)$ 的根．



### 第9题解答

{: .problem}
>  设
> 
> $$X_n(x,y)=T_{n+1}(x)T_n(y)-T_{n+1}(y)T_n(x),$$
> 
> 其中 $T_n$ 表示 Chebyshev 多项式，证明
> 
> $$X_n(x,y)=2(x-y)T_n(x)T_n(y)+X_{n-1}(x,y), \quad n\ge 1.$$
> 
> 并导出
> 
> $$\dfrac{1}{2}X_n(x,y)=(x-y)\left[
\sum\limits_{k=1}^nT_k(x)T_k(y)\right].$$

依据 $T_n(x)$ 的递推式

$$T_{n+1}=2xT_n(x)-T_{n-1}(x)$$

可以证明第一条式子．第二条式子采用裂项相消求和法．本题没什么难度．


### 第13题解答

{: .problem}
>  求函数 $f(x)=\arctan x$ 在 $[-1,1]$ 上的三次 Chebyshev 插值多项式．

4 次 Chebyshev 多项式是 $T_4(x)=8x^4-8x^2+1$，其零点是 $\cos\dfrac{\pi}{8}$，$\cos\dfrac{3\pi}{8}$，$\cos\dfrac{5\pi}{8}$，$\cos\dfrac{7\pi}{8}$．

以这四个点为插值结点得到的多项式就是三次 Chebyshev 插值多项式．



### 第16题解答

{: .problem}
> 证明：在所有首项系数为 1 的 $n$ 次多项式集合 $Q_n$ 中，Legendre 多项式 $\bar{P}_n(x)=\dfrac{2^n(n!)^2}{(2n)!}P_n(x)$ 在区间 $[-1,1]$ 上与零的平方误差最小，即
>
> $$\int_{-1}^1\vert\bar{P}_n(x)\vert^2\mathrm{d}x=\min\limits_{p_n\in Q_n}\int_{-1}^1\vert p_n(x)\vert^2\mathrm{d}x.$$

证明：因为 Legendre 多项式 $\lbrace P_k\rbrace$ 是正交多项式，故对任意 $p_n\in Q_n$，有

$$p_n=\sum\limits_{k=0}^nc_kP_k,$$

其中 $\deg p_n=n$ 且 $p_n$ 为首一多项式，所以 $c_n=\dfrac{2^n(n!)^2}{(2n)!}$．于是，由正交性得

$$\int_{-1}^1\vert p_n(x)\vert^2\mathrm{d}x=\sum\limits_{k=0}^nc_k^2\int_{-1}^1\vert P_k(x)\vert^2\mathrm{d}x \ge \int_{-1}^1c_n^2\vert P_n(x)\vert^2\mathrm{d}x.$$

等号成立条件是 $c_0=c_1=\cdots=c_{n-1}=0$．


### 第18(2)题解答

{: .problem}
>   求函数 $f(x)=\ln x$ 在 $[1,2]$ 上的一次和二次最佳平方逼近多项式，分别取函数系 $\lbrace 1,x\rbrace$ 和 $\lbrace 1,x,x^2\rbrace$．

首先，$\displaystyle \int_{1}^2x^k\mathrm{d}x=\dfrac{2^{k+1}-1}{k+1}$．

$\displaystyle \int_1^2x^k\ln x\mathrm{d}x=\dfrac{x^{k+1}}{k+1}\left(\ln x-\dfrac{1}{k+1}\right)\Big\vert_1^2=\dfrac{2^{k+1}}{k+1}\left(\ln 2-\dfrac{1}{k+1}\right)+\dfrac{1}{(k+1)^2}$．

(1) 一次多项式 $p(x)=a_0+a_1x$ ：法方程是

$$\begin{pmatrix}
1 & \frac{3}{2} \\ \frac{3}{2} & \frac{7}{3}
\end{pmatrix}\begin{pmatrix}
a_0 \\ a_1
\end{pmatrix}= \begin{pmatrix}
\int_{1}^2\ln x\mathrm{d}x \\
\int_{1}^2x\ln x\mathrm{d}x  
\end{pmatrix}= \begin{pmatrix}
2\ln 2-1 \\
2\ln 2-\frac{3}{4}
\end{pmatrix}$$

解得 $a_0=20\ln 2-\frac{29}{2}$，$a_1=9-12\ln 2$．

因此，$p_1(x)=20\ln 2-\frac{29}{2}+(9-12\ln 2)x$．

(2) 二次多项式 $p(x)=a_0+a_1x+a_2x^2$ ：法方程是

$$\begin{pmatrix}
1 & \frac{3}{2} & \frac{7}{3} \\ \frac{3}{2} & \frac{7}{3} & \frac{15}{4} \\
 \frac{7}{3} & \frac{15}{4} & \frac{31}{5}
\end{pmatrix}\begin{pmatrix}
a_0 \\ a_1 \\ a_2
\end{pmatrix}= \begin{pmatrix}
\int_{1}^2\ln x\mathrm{d}x \\
\int_{1}^2x\ln x\mathrm{d}x   \\
\int_{1}^2x^2\ln x\mathrm{d}x
\end{pmatrix}= \begin{pmatrix}
2\ln 2-1 \\
2\ln 2-\frac{3}{4} \\
\frac{8}{3}\ln 2 - \frac{7}{9}
\end{pmatrix}$$

解得 $a_0=410\ln 2-\frac{856}{3}$，$a_1=384-552\ln 2$，$a_2=180\ln 2-125$．

**注：** Matlab 代码如下，学会用```sym```表示变量．

```matlab
t = sym('2'); 
A= [1, 1.5 ,7/3; 1.5, 7/3, 15/4; 7/3,15/4,31/5];
b = [2*log(t)-1 ; 2*log(t)-3/4; 8/3*log(t)-7/9];
x=A\b;
```


### 第21题解答

{: .problem}
>  求 $f(x)=\arcsin x$ 的 Chebyshev 级数．

先设 $f(x)=a_0+\sum\limits_{j=1}^{\infty}a_jT_j(x)$，利用 $T_k(x)$ 的带权正交性，两边同乘 $T_k(x)\dfrac{1}{\sqrt{1-x^2}}$ 然后在 $[-1,1]$ 上积分，可得 $a_k$ 的表达式．

$$\arcsin x = 1-\dfrac{\pi}{2}+\sum_{j=1}^{\infty}\dfrac{2}{j^2\pi}((-1)^{j-1}+1)T_j(x).$$













