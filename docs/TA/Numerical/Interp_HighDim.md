---
layout: default
title: （待更新）插值：高维插值
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 54
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

{: .new}
> 参考书: Kincaid, Numerical Analysis, Section 6.10.

寻找多元函数的插值比一元函数的插值复杂许多, 多元问题常常会出现一些在一元问题中所没有的异常特征,
当仅有两个变量时这些特征就已经很明显了. 因此, 只讨论二元问题(两个独立变量). 

## 基本问题

在$xy$平面内给定插值点(或者结点)集合, 记为

$$(x_1,y_1),(x_2,y_2),\cdots,(x_n,y_n).$$

我们假设这$n$个点不相同, 每个点$(x_i,y_i)$存在一个对应的实数$c_i$, 目的是寻找一个光滑且容易计算的函数$F$, 使得

$$F(x_i,y_i)=c_i\qquad (1\le i\le n).$$

这里“光滑”和“容易计算”只有非正式的或者直观的含义.

## 笛卡尔网格

刚才所描述的插值问题有时可以用一元插值的**张量积(tensor product)**来求解.

我们首先来处理下面这种情况：记结点集为

$$\mathcal{N}=\{x_1,x_2,\cdots,x_p\}\times\{y_1,y_2,\cdots,y_q\}.$$

因此, $\mathcal{N}$是所有数对$(x_i,y_j)$的集合, 其中$x_i$选自第一个集合, $y_j$选自第二个集合. 换言之,

$$\mathcal{N}=\{(x_i,y_j):1\le i\le p, 1\le j\le q\}.$$

结点的这种阵列通常称为**笛卡尔网格(Descartes grid)**. 

假设我们有一个结点$x_1,x_2,\cdots,x_p$的一元多项式插值格式, 我们把它看做下列形式的一个**线性算子**$P$:

$$(Pf)(x)=\sum\limits_{i=1}^pf(x_i)u_i(x).$$

其中函数$u_i$具有**基性质**: 

$$u_i(x_j)=\delta_{ij}, \qquad 1\le i,j\le p.$$

{: .remark}
> 线性算子$P:f\mapsto Pf$是一个从函数空间$C^0$到函数空间$\mathrm{span}\lbrace u_1,\cdots,u_p\rbrace$的映射. 

例如, 在常规的多项式插值中函数$u_i$可以如下给出:

$$u_i(x)=\prod\limits_{\substack{j=1 \\ j\ne i}}^p\dfrac{x-x_j}{x_i-x_j}, \qquad 1\le i\le p.$$

注意到, 算子$P$可以被平凡地推广, 使其作用在两个或更多变量的函数上. 因此, 如果$f$是二元函数, 我们可以记

$$(\overline{P}f)(x,y)=\sum\limits_{i=1}^pf(x_i,y)u_i(x),$$

并立即可以看出$\overline{P}f$是在下列**垂直线**上插值$f$的一个二元函数:

$$L_i\triangleq\{(x_i,y): -\infty < y < \infty\}, \qquad 1\le i\le p.$$

类似地, 我们可以定义$y$分量上的算子. 假设另一个算子可用于结点$y_1,y_2,\cdots,y_q$的插值, 我们给出

$$(Qf)(y)=\sum_{i=1}^qf(y_i)v_i(y),$$

其中$v_i$是任何适当的函数且具有基性质

$$v_i(y_j)=\delta_{ij}, \qquad 1\le i,j\le q.$$

利用下式可以把$Q$推广使其作用在二元函数上:

$$(\overline{Q}f)(x,y)=\sum_{i=1}^qf(x,y_i)v_i(y).$$

$\overline{Q}f$是在下列**水平线**上插值$f$的一个二元函数:

$$L^i\triangleq\{(x,y_i): -\infty < y < \infty\}, \qquad 1\le i\le q.$$

## 布尔和

可以利用$\overline{P}$和$\overline{Q}$构造两个有用的二元插值算子: 
他们是**布尔积(Boolean product)**$\overline{PQ}$和**布尔和(Boolean sum)**$\overline{P}\oplus\overline{Q}$:

$$\overline{P}\oplus\overline{Q}=\overline{P}+\overline{Q}-\overline{PQ}.$$

根据$\overline{P}$和$\overline{Q}$的定义, 很容易推导出这些算子的详细公式: 

$$(\overline{PQ}f)(x,y)=\overline{P}(\overline{Q}f)(x,y)
=\sum\limits_{i=1}^p\sum\limits_{j=1}^qf(x_i,y_j)v_j(y)u_i(x).$$

对算子$\overline{PQ}$也会使用张量积的记号$P\otimes Q$. 
于是容易得到

$$[(\overline{P}\oplus\overline{Q})f](x,y)
=\sum_{i=1}^pf(x_i,y)u_i(x)+\sum_{j=1}^qf(x,y_j)v_j(y)
-\sum_{i=1}^p\sum_{j=1}^qf(x_i,y_j)u_i(x)v_j(y).$$

{: .problem}
> 证明: 函数$(\overline{P}\oplus\overline{Q})f$在所有水平线$L_i(1\le i\le p)$和所有垂直线$L^j(1\le j\le q)$上插值$f$, 
> 即
>
> $$[(\overline{P}\oplus\overline{Q})f](x_i,y_j) = f(x_i,y_j)$$
>
> 恒成立. 

{: .new-title}
> 例1
> 
> 给出一个二元多项式的表达式, 它在12个点处的取值如下:
>
> $$\begin{array}{|c||c|c|c|c|c|}
\hline (x,y) & (1,1)&(2,1)&(4,1)&(5,1) \\
\hline f(x,y) & 1.7 &-4.1 &-3.2&4.9   \\
\hline (x,y) &(1,3)&(2,3)&(4,3)&(5,3) \\
\hline f(x,y) &  6.1  &-4.2 & 2.3  &7.5   \\
\hline (x,y) & (1,4)&(2,4)&(4,4)&(5,4) \\
\hline f(x,y) & -5.9& 3.8& -1.7&2.5 \\ \hline
\end{array}$$

**解：** 首先看出这些结点构成一个笛卡尔网格, 因而可应用前面的方法. 根据$L^i$和$L^j$上的Lagrange基函数, 我们可以得到

$$\begin{aligned}
u_1(x)&=-\dfrac{1}{12}(x-2)(x-4)(x-5) \\
u_2(x)&=\dfrac{1}{6}(x-1)(x-4)(x-5) \\
u_3(x)&=-\dfrac{1}{6}(x-1)(x-2)(x-5) \\
u_4(x)&=\dfrac{1}{12}(x-1)(x-2)(x-4) \\
v_1(y)&=\dfrac{1}{6}(y-3)(y-4) \\
v_2(y)&=-\dfrac{1}{2}(y-1)(y-4) \\
v_3(y)&=\dfrac{1}{3}(y-1)(y-3)
\end{aligned}$$

因此多项式插值是

$$\begin{aligned}
F(x,y)&=u_1(x)[1.7v_1(y)+6.1v_2(y)-5.9v_3(y)] \\
&\quad + u_2(x)[-4.1v_1(y)-4.2v_2(y)+3.8v_3(y)] \\
&\quad + u_3(x)[-3.2v_1(y)+2.3v_2(y)-1.7v_3(y)] \\
&\quad + u_4(x)[4.9v_1(y)+7.5v_2(y)+2.5v_3(y)] 
\end{aligned}$$

## 张量积

如果把例1的函数$F$表示成项$x^iy^j$的和, 那么会出现下列12项:

$$1,x,x^2,x^3,y,xy,x^2y,x^3y,y^2,xy^2,x^2y^2,x^3y^2. \tag{1}$$

这样, 我们用二元多项式的12维子空间进行插值. 这个子空间特有的记号是$\Pi_3\otimes \Pi_2$, 
($\Pi_k$表示不超过$k$次的多项式全体), 它是两个线性空间的张量积, 可由所有如下形式的函数组成:

$$(x,y)\mapsto\sum_{i=1}^ma_i(x)b_i(y), \qquad \text{其中}a_i\in \Pi_3, b_i\in \Pi_2.$$

不难证明$(1)$式中的函数构成这个空间的一组基. 

{: .remark}
> 要强调的一点是刚才概述的理论可应用于一般的函数$u_i$和$v_j$, 而并不仅仅只应用于多项式, 它们所需要的只是基性质.

## 几何图形

结点怎么样分布才能构建出多元插值？

## Newton格式

## Shepard插值

{: .note}
> Shepard函数在广义有限元方法中的应用.

## 三角剖分方法


## 移动最小二乘法

