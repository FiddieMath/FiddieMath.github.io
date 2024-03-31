---
layout: default
title: 第4周作业+补充习题
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 4
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


# 第4周作业

林成森《数值计算方法》第四章习题17、18、20、21、24、27、28(3)、32、36.


# 解答

## 第17题

用带余项的Lagrange插值公式，或者用(3.11)式．

## 第18题

用Newton均差的迭代定义式(3.5)进行归纳：

$$f[x,x_1,\cdots,x_n]=\dfrac{f[x_1,x_2,\cdots,x_n]-f[x,x_1,\cdots,x_{n-1}]}{x_n-x}.$$

注意 $x_i$ 是 $f[x,x_1,\cdots,x_n]$ 的根．

## 第20题

134，2674，1，0．前两个直接列Newton差商表进行计算，后两个利用第17题．

## 第21题

重要习题！你懂的！记

$$f(x)=a\prod\limits_{j=1}^n(x-x_j),$$

先写出$f'(x)$的表达式，取$x=x_i$，得到

$$f'(x_i)=a\prod\limits_{j\ne i}(x_i-x_j)$$

发现它跟Lagrange插值多项式很像．接下来利用第8题或第17题的结论．

## 第24题

计算得

$$\begin{aligned}
N_2(x)&=3-\dfrac{1}{4}x(x-1), \\
N_3(x)&=3-\dfrac{1}{4}x(x-1)-\dfrac{7}{6}x(x-1)(x-2).
\end{aligned}$$

## 第27题

用$\Delta^2$的定义，把求和的左边写成裂项形式，然后求和．

## 第28(3)题

注意

$$\begin{aligned}
\Delta \sin k\alpha&=\sin(k+1)\alpha-\sin k\alpha \\
&=2\sin\dfrac{\alpha}{2}\cos(\dfrac{\alpha}{2}+k\alpha),
\end{aligned}$$

这里欲证式子等号右边分母需补上一个2．

## 第32题

三次Newton前差和后差插值多项式分别是

$$\begin{aligned}
N_3(x)&=N_3(0+s)=1+s+\dfrac{1}{2}s(s-1)+\dfrac{1}{6}s(s-1)(s-2), \\
N_3(x)&=N_3(3+t)=8+4t+t(t+1)+\dfrac{1}{6}t(t+1)(t+2).
\end{aligned}$$

这两个多项式是相同的（替换 $t=x-3$，$s=x-0$ 之后）

取 $s=0.25$，$t=-2.75$，都能算出 $N_3(0.25)=\dfrac{155}{128}$．

取 $s=2.5$，$t=-0.5$，都能算出 $N_3(2.5)=\dfrac{91}{16}$．

## 第36题

这是重点题！务必搞懂！

先假设

$$p(x)=f_1+f_1'(x-x_1)+C(x-x_1)^2,$$

代入$x=x_2$得

$$C=\dfrac{f_2-f_1-f_1'(x_2-x_1)}{(x_2-x_1)^2}.$$

这样就能构造出一个满足条件的不超过二次的多项式．

证明唯一性：仿照4.5节的“定理”，用 Rolle 定理来证明，最终就能导出余项表达式．

$$f(x)-p(x)=\dfrac{f^{(3)}(\xi)(x-x_1)^2(x-x_2)}{6}.$$

**【错解】** 有同学没有仿照4.5节的“定理”的证明，直接就写

$$f(x)-p(x)=\dfrac{f^{(3)}(\xi)(x-x_1)^3}{6}$$

这是不对的．更有同学得出一些奇怪的结果，可能是没有理解好构造

$$g(t)=f(t)-p(t)-K(t-x_1)^2(t-x_2)$$

的步骤．




# 第4周答疑

## 补充习题（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1．** 已知$f(x)$在区间$[0,2]$上具有三阶连续导数，设

$$g(x)=f(0)+(f(1)-f(0))x+\dfrac{f(2)-2f(1)+f(0)}{2}(x^2-x)$$

证明：$\max\limits_{x\in[0,2]}\vert f(x)-g(x)\vert  \le \dfrac{\sqrt{3}}{27}\max\limits_{x\in[0,2]}\vert f^{(3)}(x)\vert$．

&nbsp;

&nbsp;

**2．【UC San Diego PhD Qualifying Exam, Sep 2007】**

设 $k\ge 1$ 是整数，$p_k(x)$ 是插值点为$(x_0,y_0)$, $(x_1,y_1)$, $\cdots$, $(x_k,y_k)$的Lagrange插值多项式，$q_k(x)$ 是插值点为$(x_1,y_1)$, $(x_2,y_2)$, $\cdots$, $(x_{k+1},y_{k+1})$的Lagrange插值多项式．定义

$$r_{k+1}(x)=\dfrac{(x-x_0)q_k(x)-(x-x_{k+1})p_k(x)}{x_{k+1}-x_0},$$

证明：$r_{k+1}(x)$是插值点为$(x_0,y_0)$, $(x_1,y_1)$, $\cdots$, $(x_k,y_k)$, $(x_{k+1},y_{k+1})$的插值多项式．

&nbsp;

&nbsp;

**3．** 设$x_0 < x_1 < \cdots < x_n$，并且 $f$ 连续可微，证明：

$$\dfrac{\partial}{\partial x_i}f[x_0,x_1,\cdots,x_n] = f[x_0,x_1,\cdots,x_{i-1},x_i,x_i,x_{i+1},\cdots,x_n].$$

&nbsp;

&nbsp;

**4．** 本题是 Hermite 插值多项式的有关补充内容——插值零的定义及性质．

{: .new-title}
> Definition
> 
> **定义：** 若对于在基点 $x_0$, $x_1$, $\cdots$, $x_n$ 中重复出现 $k$ 次或更多次的每一点 $\xi$，都有 $f^{(k-1)}(\xi)=0$，则称 $f$ 在点 $x_0$, $x_1$, $\cdots$, $x_n$ 上 **插值零**．
> 
> 例如，我们称$f$在点1, 3, 8, 1, 13, 1, 8上插值零，如果
> 
> $$f(1)=f(3)=f(8)=f'(1)=f(13)=f''(1)=f'(8)=0.$$
> 
> 如果两个函数 $f$ 和 $g$ 使得 $f-g$ 在点  $x_0$, $x_1$, $\cdots$, $x_n$ 上插值零，我们称 $f$ 在点 $x_0$, $x_1$, $\cdots$, $x_n$ 上插值 $g$（或者 $g$ 在点 $x_0$, $x_1$, $\cdots$, $x_n$ 上插值 $f$）．

回答如下问题：

(1) 证明：一个多项式在点 $x_0$, $x_1$, $\cdots$, $x_n$ （允许重复）上插值零的充分必要条件是它包含因子 $\prod\limits_{j=0}^n(x-x_j)$．

(2) 设 $f$ 在基点 $x_0$, $x_1$, $\cdots$, $x_n$ 上插值 $g$，并且 $h$ 在这些点上插值零，证明：$f\pm ch$ 在这些点上插值 $g$．

(3) 证明：若 $f$ 在基点 $x_0$, $x_1$, $\cdots$, $x_n$ 上插值零，则 $f$ 在基点 $x_0$, $x_1$, $\cdots$, $x_{n-1}$ 上也插值零．

{: .new-title}
> Definition
> 
> **定义：** 设 $K$ 是域，一个 **$K$-代数** $A$ 满足如下条件：
>
> (i) $A$ 是含单位元的环；
>
> (ii) $A$ 是 $K$-线性空间，满足对任意 $k\in K$，$a,b\in A$，都有 $k(ab)=(ka)b=a(kb)$．
>
> **例1：** 包含 $K$ 的交换环是一个 $K$-代数，比如二元多项式环 $K[X,Y]$、形式幂级数环 $K[[X]]$．
>
> **例2：** 环 $M_n(K)$ 的加法和乘法分别用矩阵加法和矩阵乘法定义，则 $M_n(K)$ 是 $K$-代数．

(4) 给定基点 $x_0$, $x_1$, $\cdots$, $x_n$．证明：在这些点上插值零的函数集合构成一个 $\mathbf{R}$-代数．

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## 补充习题提示

**1．** 提示：把 $g(x)$ 写成Newton插值多项式，然后用带余项的Lagrange插值多项式．

**2．** 提示：验证 $y_i=r_{k+1}(x_i)$，$i=0,1,\cdots,k+1$．

**3．** 提示：偏导数的定义和 Newton 均差递推定义式或许能带来帮助．

