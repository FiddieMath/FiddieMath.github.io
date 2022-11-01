---
layout: default
title: 补充内容：期中复习思考题的解答
parent: 数学分析A
grand_parent: 助教工作
nav_order: 10
---

{% raw %}

# 问题

## 一、判断题

1. 设$\lim\limits_{n\to\infty}a_n=\alpha$, $\lim\limits_{n\to\infty}b_n=\beta$, 如果$a_n>b_n$, 则$\alpha>\beta.$
2. 如果对任意$p\in\mathbb{N}$, 都有$\lim\limits_{n\to\infty}\vert a_{n+p}-a_n\vert =0$, 则$\lbrace a_n\rbrace $是Cauchy列.
3. 设$\lim\limits_{x\to x_0}g(x)=y_0$, $\lim\limits_{y\to y_0}f(y)=\alpha$, 则$\lim\limits_{x\to x_0}f(g(x))=\alpha.$ 
4. 设$f$在$x_0$附近有定义, 如果对任何收敛于$x_0$的数列$\lbrace x_n\rbrace $, 数列$\lbrace f(x_n)\rbrace $都收敛, 则$f$在$x_0$连续.
5. 如果$f$在区间中每一点都局部单调, 则$f$在区间上单调.
6. $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall\varepsilon>0, \exists N>0$, 使得当$n\ge 2023N$时, 有$\vert a_n-A\vert \le 2022\varepsilon.$
7. $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall\varepsilon\ge 0, \exists N>0$, 使得当$n\ge N$时, 有$\vert a_n-A\vert \le \varepsilon.$
8. $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall\varepsilon\in(0,1), \exists N>0$, 使得当$n\ge N$时, 有$\vert a_n-A\vert \le 2\varepsilon.$
9. $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \exists N>0$, 使得$\forall \varepsilon\in(0,1), \forall n>N$, 有$\vert a_n-A\vert  < \varepsilon.$ 
10. $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall \varepsilon>0$, $\exists N\ge 0$, 使得当$n\ge 2N$时, $A-\varepsilon < \inf\limits_{k\ge n} a_k\le \sup\limits_{k\ge n}a_k < A+\varepsilon.$
11. $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall \varepsilon>0$, $\exists N\ge 0$, 使得$A-\varepsilon < \inf\limits_{n\ge N} a_n\le \sup\limits_{n\ge N}a_n < A+\varepsilon.$
12.  $\lbrace a_n\rbrace $收敛$\Longleftrightarrow \forall \varepsilon>0$, $\exists N>0$, 使得$\sup\limits_{m,n>N}\vert a_m-a_n\vert \le\varepsilon.$
13.  设数列$\lbrace a_n\rbrace $有界, 则: $\lbrace a_n\rbrace $收敛$\Longleftrightarrow \sup\limits_{n\ge 1}\inf\limits_{k\ge n}a_k=\inf\limits_{n\ge 1}\sup\limits_{k\ge n}a_k.$

## 二、解答题

**1.** 计算

$$\lim\limits_{n\to\infty}\left(1-\dfrac{1}{n}+\dfrac{1}{n^2}\right)^n.$$

**2.** 设$a_1\in\mathbb{R}$, $a_{n+1}=\cos a_n$. 证明数列$\lbrace a_n\rbrace $收敛, 
且其极限位于区间$(\sqrt{3}-1,1)$中.

**3.** 设$f\in C^0[a,b]$, 若$\forall x\in[a,b)$, $\exists x'>x$, 使得$f(x')\ge f(x)$,
证明$f(b)\ge f(a)$.

**4.** 设$\varepsilon_n>0$, 且$\sum\limits_{n=1}^{\infty}\varepsilon_n$收敛,
$x_n\ge 0$, 且$x_{n+1}\le x_n+\varepsilon_n$. 证明$\lbrace x_n\rbrace $收敛. 

{: .remark}
> $\sum\limits_{n=1}^{\infty}\varepsilon_n$收敛, 指的是对于$A_n=\sum\limits_{k=1}^{n}\varepsilon_k$, 数列$\lbrace A_n\rbrace $收敛. 

# 解答

## 一、判断题

{: .problem}
> $\color{blue}{\mathbf{\text{1.}}}$ 设$\lim\limits_{n\to\infty}a_n=\alpha$, $\lim\limits_{n\to\infty}b_n=\beta$, 如果$a_n>b_n$, 则$\alpha>\beta.$

错误. 回顾极限的保号性(命题2.1.5). 

> $\color{purple}{\mathbf{\text{Proposition 2.1.5}}}$ 设数列$\lbrace a_n\rbrace$收敛到$\alpha$, 
> 数列$\lbrace b_n\rbrace$收敛到$\beta$, 如果存在$N_0$, 当$n>N_0$时$a_n\ge b_n$, 则$\alpha\ge \beta$. 

等号成立的一个典型的例子就是取$a_n=\dfrac{1}{n}$, $b_n=0$. 

{: .problem}
> $\color{blue}{\mathbf{\text{2.}}}$ 如果对任意$p\in\mathbb{N}$, 都有$\lim\limits_{n\to\infty}\vert a_{n+p}-a_n\vert =0$, 则$\lbrace a_n\rbrace $是Cauchy列.

错误. 这是习题2.3的第1题. 考虑

$$a_n=1+\dfrac{1}{2}+\cdots+\dfrac{1}{n}.$$

则对任意**固定**的正整数$p$, 

$$|a_{n+p}-a_n|=\dfrac{1}{n+1}+\cdots+\dfrac{1}{n+p} \le \dfrac{p}{n} \to 0(n\to\infty),$$

所以$\lim\limits_{n\to\infty}\vert a_{n+p}-a_n\vert =0$, 但是$\left\lbrace a_n\right\rbrace$不是Cauchy列. 

{: .problem}
> $\color{blue}{\mathbf{\text{3.}}}$ 设$\lim\limits_{x\to x_0}g(x)=y_0$, $\lim\limits_{y\to y_0}f(y)=\alpha$, 则$\lim\limits_{x\to x_0}f(g(x))=\alpha.$ 

错误. 回顾复合函数的连续性(命题3.3.3):

> $\color{purple}{\mathbf{\text{Proposition 3.3.3}}}$ 设函数$f(y)$在$y_0$连续, 函数$g(x)$在$x_0$处的极限为$y_0$, 
> 则$f(g(x))$在$x_0$处的极限为$f(y_0)$. 

本题把上述命题的连续性条件变为了极限存在的条件. (注意连续性的条件是$\lim\limits_{x\to x_0}f(x)=f(x_0)$, 
这里把连续性条件中的$f(x_0)$换成了$\alpha$)

我们考虑函数极限是在去心开邻域$V(x_0,\delta)=(x_0-\delta,x_0)\cup(x_0,x_0+\delta)$中考虑的! 

但极限存在不代表连续, 例如函数

$$f(x)=\left\{\begin{aligned}
&1, &&x=0, \\
&0, &&x\ne 0,
\end{aligned}\right.$$

它满足$\lim\limits_{y\to 0}f(y)=0$, 但是在$0$处不连续. 

令$g(x)=0$(常函数), 则$f(g(x))=f(0)=1$恒成立, 于是$\lim\limits_{x\to x_0}f(g(x))=1 \ne 0$. 

{: .problem}
> $\color{blue}{\mathbf{\text{4.}}}$ 设$f$在$x_0$附近有定义, 如果对任何收敛于$x_0$的数列$\lbrace x_n\rbrace $, 数列$\lbrace f(x_n)\rbrace $都收敛, 则$f$在$x_0$连续.

正确. 回顾书上第58页的注(在定义3.3.2前面)以及Heine定理(定理3.1.8): 

> $\color{purple}{\mathbf{\text{Theorem 3.1.8(Heine)}}}$ 设函数$f$在$x_0$的一个空心开邻域中有定义, 
> 则$f$在$x_0$处的极限为$\alpha$当且仅当对空心开邻域中任何收敛于$x_0$的数列$\lbrace x_n\rbrace$,
> 都有$\lim\limits_{n\to\infty}f(x_n)=\alpha$. 

根据Heine定理以及本题条件, 可知$f$在$x_0$处的极限存在. 
假设

$$\lim\limits_{x\to x_0}f(x)=\alpha.$$

下面, 我们构造$\lbrace x_n\rbrace$如下: (如果$x_{2k-1}$不在定义域内, 而$x_{2k+1}$在定义域内, 
那么我们就从$\lbrace x_{2k+1}\rbrace$开始看. 有限项的改变不会影响极限.)

$$x_{2n}=x_0, \qquad x_{2n-1}=x_0+\dfrac{1}{n}, \qquad n\in\mathbb{N}, $$

则$\lbrace f(x_n)\rbrace$收敛于$\alpha$, 从而它的所有子列都收敛于$\alpha$, 
即$\lbrace f(x_{2n})\rbrace$收敛于$\alpha$, 即必有

$$f(x_0)=\alpha,$$

从而$f$在$x_0$处连续. 


{: .problem}
> $\color{blue}{\mathbf{\text{5.}}}$ 如果$f$在区间中每一点都局部单调, 则$f$在区间上单调.

错误. 考虑函数

$$f(x)=\left\{\begin{aligned}
&x, &&x\in[0,1], \\
&1, &&x\in[1,2], \\
&3-x, &&x\in[2,3], \\
&0, &&\text{其他}
\end{aligned}\right.$$

{: .remark}
> 如果把“局部单调”和“单调”分别改成“局部严格单调”和“严格单调”, 那么结论正确. 证明如下：
> 
> **(1)** 先考虑闭区间. 
> 
> 假设$f$定义在闭区间$I$上. 对任意$x\in I$, 根据局部单调的定义, 存在$\delta_x>0$, 
使得$f$在区间$(x-\delta_x,x+\delta_x)$中是单调函数. 我们考虑区间$I$的开覆盖如下:
> 
> $$I=\bigcup\limits_{x\in I}(x-\delta_x,x+\delta_x),$$
> 
> 由Heine-Borel定理(有限覆盖定理, 即闭区间的开覆盖必有有限子覆盖), 我们可以找到有限个点$x_1,\cdots,x_n$, 使得
> 
> $$I=\bigcup\limits_{i=1}^n(x_i-\delta_{x_i}, x_i+\delta_{x_i}).$$
> 
> 注意, $f$在每个区间$(x_i-\delta_{x_i}, x_i+\delta_{x_i})$上都是单调函数.
不妨设$f$在某个$(x_i-\delta_{x_i},x_i+\delta_{x_i})$单调递增(单调递减情形完全对偶), 
那么根据
> 
> $$(x_k-\delta_{x_k},x_k+\delta_{x_k})\cap (x_{k+1}-\delta_{x_{k+1}}, x_{k+1}+\delta_{x_{k+1}})\ne\varnothing,$$ 
> 
> 可知$f$在$(x_{i-1}-\delta_{x_{i-1}},x_{i-1}+\delta_{x_{i-1}})$以及$(x_{i+1}-\delta_{x_{i+1}},x_{i+1}+\delta_{x_{i+1}})$也是单调递增(**注：**如果把“严格单调”改成“单调”, 那这一步是错的, 因为局部常函数同时是递增或者递减的). 
这样不断进行下去可知$f$在$I$上单调递增. 
> 
> **(2)** 对于一般的区间$I$, 假设$x_1,x_2\in I$, 满足$x_1 < x_2$. 由于闭区间$[x_1,x_2]$上的每个点都是局部单调的, 不妨设在某一个点是局部单调递增. 
利用(1)中证明的结论可知函数$f(x)$在区间$[x_1,x_2]$上是单调递增的, 于是$f(x_1) < f(x_2)$.
从而$f(x)$在$I$上是单调递增的. 
$\square$

{: .problem}
> $\color{blue}{\mathbf{\text{6.}}}$ $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall\varepsilon>0, \exists N>0$, 使得当$n\ge 2023N$时, 有$\vert a_n-A\vert \le 2022\varepsilon.$
> 
> $\color{blue}{\mathbf{\text{7.}}}$ $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall\varepsilon\ge 0, \exists N>0$, 使得当$n\ge N$时, 有$\vert a_n-A\vert \le \varepsilon.$
> 
> $\color{blue}{\mathbf{\text{8.}}}$ $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall\varepsilon\in(0,1), \exists N>0$, 使得当$n\ge N$时, 有$\vert a_n-A\vert \le 2\varepsilon.$

这些都是正确的命题, 回顾2.1节第1题. 

{: .problem}
> $\color{blue}{\mathbf{\text{9.}}}$ $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \exists N>0$, 使得$\forall \varepsilon\in(0,1), \forall n>N$, 有$\vert a_n-A\vert  < \varepsilon.$ 

错误. 极限定义中$\varepsilon$和$N$的引入顺序不能变, 一定要清楚: 是$N$依赖于$\varepsilon$, 而不是$\varepsilon$依赖于$N$. 

我们就取$a_n=\dfrac{1}{n}$, $A=0$, 那么$\lim\limits_{n\to\infty}a_n=A$, 
但是右边不成立. 

右边的否定为：对任意$N>0$, 存在$\varepsilon\in(0,1)$, 存在$n>N$, 有$\vert a_n-A\vert \ge\varepsilon$. 

事实上, 对任意$N>0$, 我们取$\varepsilon=\dfrac{1}{2N+2}$, $n=N+1$, 
则

$$|a_n-A|=\dfrac{1}{N+1} > \dfrac{1}{2N+2} = \varepsilon,$$

也就是说右边的否定成立, 即右边不成立. 

{: .remark}
> 如果右边成立, 那么能推出$\lbrace a_n\rbrace$在某一项开始是常数列. 
> 
> 下面我们假设存在$N>0$, 使得对任意$\varepsilon\in(0,1)$与任意$n>N$, 都有$\vert a_n-A\vert < \varepsilon$.
> 
> 这样, 取定$N$以后, 根据$\varepsilon$的任意性, 可知当$n>N$时必有$a_n=A$. 
> 所以$\lbrace a_n\rbrace$在第$N+1$项开始是常数列. 

{: .problem}
> $\color{blue}{\mathbf{\text{10.}}}$ $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall \varepsilon>0$, $\exists N\ge 0$, 使得当$n\ge 2N$时, $A-\varepsilon < \inf\limits_{k\ge n} a_k\le \sup\limits_{k\ge n}a_k < A+\varepsilon.$

“$\Rightarrow$”方向是对的, 用定理2.2.3可以马上推出来. 

> $\color{purple}{\mathbf{\text{Theorem 2.2.3}}}$ 设$\lbrace a_n\rbrace$为有界数列, 
> 则下列命题等价:
>
> (1)$\lbrace a_n\rbrace$收敛;
> 
> (2)$\lbrace a_n\rbrace$的上极限和下极限相等;
> 
> (3)$\lim\limits_{n\to\infty}\Big(\sup\limits_{k\ge n}a_k - \inf\limits_{k\ge n}a_k\Big)=0.$

对于“$\Leftarrow$”方向, 假设条件成立, 则$\forall \varepsilon>0$, $\exists N\ge 0$, 使得当$n\ge 2N$时, 

$$0\le \sup\limits_{k\ge n}a_k - \inf\limits_{k\ge n}a_k < 2\varepsilon.$$

所以关于$n$的数列$\lbrace \sup\limits_{k\ge n}a_k - \inf\limits_{k\ge n}a_k\rbrace$收敛于$0$, 
根据上述定理2.2.3(的证明过程)可知$\lbrace a_n\rbrace$收敛于$A$. 

{: .problem}
> $\color{blue}{\mathbf{\text{11.}}}$ $\lim\limits_{n\to\infty}a_n=A \Longleftrightarrow \forall \varepsilon>0$, $\exists N\ge 0$, 使得$A-\varepsilon < \inf\limits_{n\ge N}a_n \le \sup\limits_{n\ge N}a_n < A+\varepsilon.$

首先“$\Leftarrow$”方向可以马上推出来. 如果右边成立, 那么$\forall \varepsilon>0$, $\exists N\ge 0$, 当$m\ge N$时, 有

$$A-\varepsilon < \inf\limits_{n\ge N}a_n \le a_m \le \sup\limits_{n\ge N}a_n < A+\varepsilon.$$

所以$\lim\limits_{n\to\infty}a_n=A$. 

对于“$\Rightarrow$”方向, 完全仿照定理2.2.3来证明即可. 假设左边成立, 那么$\forall \varepsilon>0$, $\exists N\ge 0$, 当$n\ge N$时, 有

$$A-\varepsilon < a_n < A+\varepsilon.$$

由确界的定义, 当$n\ge N$时, 有

$$A-\varepsilon \le \inf\limits_{k\ge n}a_k \le \sup\limits_{k\ge n}a_k < A + \varepsilon.$$

特别的, 上式对$n=N$也对, 即

$$A-\varepsilon \le \inf\limits_{k\ge N}a_k \le \sup\limits_{k\ge N}a_k < A + \varepsilon.$$

所以右边成立. 

{: .problem}
> $\color{blue}{\mathbf{\text{12.}}}$ $\lbrace a_n\rbrace $收敛$\Longleftrightarrow \forall \varepsilon>0$, $\exists N>0$, 使得$\sup\limits_{m,n>N}\vert a_m-a_n\vert \le\varepsilon.$

正确. 这是Cauchy准则的一个等价表述. 

{: .remark}
> “任意$m,n>N$”这样的说法都可以用上确界来代替, 也就是说
> 
> $$\forall m,n>N, \text{都有}|a_m-a_n| < \varepsilon$$
> 
> 可以等价写成
> 
> $$\sup\limits_{m,n>N}|a_m-a_n| \le \varepsilon. $$
> 
> 这对后面理解一致连续和(逐点)连续的关系也很有帮助.



{: .problem}
> $\color{blue}{\mathbf{\text{13.}}}$ 设数列$\lbrace a_n\rbrace $有界, 则: $\lbrace a_n\rbrace $收敛$\Longleftrightarrow \sup\limits_{n\ge 1}\inf\limits_{k\ge n}a_k=\inf\limits_{n\ge 1}\sup\limits_{k\ge n}a_k.$

正确. 回顾定理2.2.1: 

> $\color{purple}{\mathbf{\text{Theorem 2.2.1}}}$ 设$\lbrace a_n\rbrace$为单调数列. 
>
> (1)如果$\lbrace a_n\rbrace$为单调递增数列, 则
> $\lim\limits_{n\to\infty}a_n=\sup\limits_{k\ge 1}a_k.$
> 
> (2)如果$\lbrace a_n\rbrace$为单调递减数列, 则
> $\lim\limits_{n\to\infty}a_n=\inf\limits_{k\ge 1}a_k.$

由于关于$n$的数列$\lbrace \inf\limits_{k\ge n}a_k\rbrace$是单调递增的, 所以根据定理2.2.1, 

$$\lim\limits_{n\to\infty}\inf\limits_{k\ge n}a_k
= \sup\limits_{n\ge 1}\inf\limits_{k\ge n}a_k,$$

类似我们有

$$\lim\limits_{n\to\infty}\sup\limits_{k\ge n}a_k
= \inf\limits_{n\ge 1}\sup\limits_{k\ge n}a_k,$$

紧接着用定理2.2.3即可.

## 二、解答题

### 第1题

{: .problem}
> $\color{blue}{\mathbf{\text{1.}}}$ 计算$\lim\limits_{n\to\infty}\left(1-\dfrac{1}{n}+\dfrac{1}{n^2}\right)^n.$

**解：** 首先注意到

$$\left(1-\dfrac{1}{n}+\dfrac{1}{n^2}\right)^n\ge \left(1-\dfrac{1}{n}\right)^n$$

并且

$$\begin{aligned}
\left(1-\dfrac{1}{n}+\dfrac{1}{n^2}\right)^n
=\left(1-\dfrac{n-1}{n^2}\right)^n 
=\left(1-\dfrac{1}{\frac{n^2}{n-1}}\right)^{\frac{n^2}{n-1}\cdot\frac{n-1}{n}} 
\le \left(1-\dfrac{1}{\frac{n^2}{n-1}}\right)^{\frac{n^2}{n-1}},
\end{aligned}$$

所以利用夹逼准则可知

$$\lim\limits_{n\to\infty}\left(1-\dfrac{1}{n}+\dfrac{1}{n^2}\right)^n=e^{-1}.$$


### 第2题

{: .problem}
> $\color{blue}{\mathbf{\text{2.}}}$ 设$a_1\in\mathbb{R}$, $a_{n+1}=\cos a_n$. 证明数列$\lbrace a_n\rbrace $收敛, 
且其极限位于区间$(\sqrt{3}-1,1)$中.

这一题改编自习题3.1的第6题. 

**证明：** 首先, $\vert a_2\vert \le 1$, $0 < \cos 1\le a_3 \le 1$, 于是用归纳法不难证明: 从第3项开始, 
都有 $0 < \cos 1 \le a_n \le 1$. 

假设$A\in(0,1)$满足$A = \cos A$. 这个$A$是存在的, 因为函数$f(x)=x-\cos x$满足$f(0)=-1 < 0$, $f(1)=1-\cos 1>0$, 根据介值定理, 存在$A$使得$f(A)=0$, 即$A=\cos A$. 

下面, 我们证明$\lbrace a_n\rbrace$收敛于$A$. 事实上, 注意到当$n\ge 4$时, 利用不等式$\vert \sin x\vert \le \vert x\vert$可知

$$\begin{aligned}
|a_n-A| &= |\cos a_{n-1}-\cos A| \\
&=\left|-2\sin\dfrac{a_{n-1}-A}{2}\sin\dfrac{a_{n-1}+A}{2}\right| \\
&\le \dfrac{|a_{n-1}+A|}{2}|a_{n-1}-A| \\
&\le \dfrac{1+A}{2}|a_{n-1}-A|.
\end{aligned}$$

所以

$$|a_n-A| \le \left(\dfrac{1+A}{2}\right)^{n-3}|a_3-A|.$$

注意$\dfrac{1+A}{2} < 1$, 所以上式不等号右边趋于$0$, 于是$\lim\limits_{n\to\infty}a_n = A$,
即$\lbrace a_n\rbrace$极限存在. 

下面证明$A\in(\sqrt{3}-1,1)$. 利用不等式$\vert \sin x\vert < \vert x\vert(x\ne 0)$可知

$$\cos x = 1 - 2\sin^2\dfrac{x}{2} > 1 - \dfrac{x^2}{2},$$

所以

$$A = \cos A > 1-\dfrac{A^2}{2},$$

这个不等式的解为$A > \sqrt{3} - 1$或$A < -\sqrt{3}-1$. 
排除掉负的部分, 可知$A$所在的范围是$\sqrt{3}-1 < A < 1.$


### 第3题

{: .problem}
> $\color{blue}{\mathbf{\text{3.}}}$ 设$f\in C^0[a,b]$, 若$\forall x\in[a,b)$, $\exists x'>x$, 使得$f(x')\ge f(x)$,
证明$f(b)\ge f(a)$.

**证明：** (反证法)假设$f(b) < f(a)$. 由条件, 存在$a_1>a$使得$f(a_1)>f(a)$.
而$f(a_1)>f(b)$, 于是根据介值定理可知存在$x\in[a_1,b]$使得$f(x)=f(a)$, 或者说下面这个集合不是空集:

$$A=\{x|x\in[a,b), f(x)=f(a)\}.$$

我们取$c=\sup A$, 则根据上确界定义, 对任意正整数$n$, 存在$x_n\in A$, 使得

$$x_n \le c \le x_n+\dfrac{1}{n}.$$

于是$\lim\limits_{n\to\infty}x_n=c$. 根据$f\in C^0[a,b]$以及Heine定理可知

$$f(c)=\lim\limits_{n\to\infty}f(x_n)=f(a),$$

**(注意$f(x_n)=f(a)$恒成立! )**

所以$c\in A$并且$c=\max A$. 再由题目条件, 存在$c'>c$使得$f(c')\ge f(c)=f(a)$, 
所以根据连续函数介值定理可知存在$c_1\in[c',b]$使得$f(c_1)=f(c)=f(a)$, 
也就是说我们找到了$c_1\ge c'>c$满足$f(c_1)=f(a)$. 这与$c=\max A$矛盾. $\square$

{: .remark}
> 在用反证法的时候, 构造一个数集, 然后在这个集合中取上确界$c$, 紧接着推出能找到比$c$还大的元素在这个集合中, 推出与$c$是上确界矛盾. 这个证明方法在有些情况下还是非常好用的. 
> 
> 事实上, 在证明**定理3.4.2(零值定理, Bolzano)** 的时候, 就用到了这个证明技巧. 请读者回顾课本.


{: .remark}
> 本题的其他做法：
> 
> 1. 反证法, 考虑$A=\lbrace x\vert \text{对任意}y\in[x,b], \text{都有}f(y) < f(a)\rbrace$.
> 
> 2. 考虑$A=\lbrace x\vert x\in[a,b], f(x)\ge f(a)\rbrace$, 然后证明$b\in A$. 



### 第4题

{: .problem}
> $\color{blue}{\mathbf{\text{4.}}}$ 设$\varepsilon_n>0$, 且$\sum\limits_{n=1}^{\infty}\varepsilon_n$收敛,
$x_n\ge 0$, 且$x_{n+1}\le x_n+\varepsilon_n$. 证明$\lbrace x_n\rbrace $收敛. 

**证明：** 设$A_n=\sum\limits_{k=1}^{n}\varepsilon_k$, 则数列$\lbrace A_n\rbrace$收敛, 
记$\lim\limits_{n\to\infty}A_n=A$. 

由于$\varepsilon_n>0$, 所以$A_n < A$. 

对任意正整数$m,n$, 当$m>n$时, 

$$\begin{aligned}
x_{m}-x_n&=\sum\limits_{k=n}^{m-1}(x_{k+1}-x_k) \\
&\le \sum\limits_{k=n}^{m-1}\varepsilon_k \\
&=A_{m-1}-A_{n-1}.
\end{aligned}$$

再结合$x_n\ge 0$与$A_n < A$可得

$$-A < x_m-A_{m-1} \le x_n-A_{n-1}.$$

所以$\lbrace x_n-A_{n-1}\rbrace$是递减数列并且有下界, 故$\lbrace x_n-A_{n-1}\rbrace$极限存在.
从而

$$\lim\limits_{n\to\infty}x_n=\lim\limits_{n\to\infty}(x_n-A_{n-1})
+\lim\limits_{n\to\infty}A_{n-1}$$

也极限存在. $\square$

{% endraw %}
