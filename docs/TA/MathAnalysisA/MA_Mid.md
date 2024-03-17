---
layout: default
title: 补充内容：三道题的解答
parent: 数学分析A
grand_parent: 助教工作
nav_order: 12
---

{% raw %}

{: .problem}
> $\color{blue}{\mathbf{\text{1.}}}$ 设$f$是在$[a,b]$中定义的函数, 且存在常数$L>0$, 使得
>
> $$|f(x)-f(y)|\le L|x-y|, \qquad \forall x,y\in[a,b].$$
>
> 设$f(a) < \mu < f(b)$. 令$c_1=a$, 当$n\ge 1$时, $c_{n+1}=c_n+\dfrac{1}{L}[\mu-f(c_n)]$. 
> 研究数列$\lbrace c_n\rbrace$是否收敛.

**证明：** 由条件, $f(c_1)=f(a) < \mu$且$a\le c_1 < b$. 

下面用数学归纳法证明$f(c_n)\le \mu$且$a\le c_n < b$. 

假设$f(c_n)\le \mu$且$a\le c_n < b$, 下证$f(c_{n+1})\le \mu$且$a\le c_{n+1} < b$. 事实上, 易知

$$c_{n+1}\ge c_n$$

并且

$$\begin{aligned}
c_{n+1}&=c_n+\dfrac{1}{L}(\mu-f(c_n)) \\
& < c_n+\dfrac{1}{L}(f(b)-f(c_n)) \\
& \le c_n+\dfrac{1}{L}\cdot L|b-c_n| && (c_n < b) \\
& = c_n+(b-c_n)=b. 
\end{aligned}$$

所以$a\le c_n \le c_{n+1} < b$. 另外, 

$$\begin{aligned}
f(c_{n+1})&=f\left(c_n+\dfrac{1}{L}(\mu-f(c_n))\right) \\
&\le f(c_n)+L\cdot\dfrac{1}{L}|\mu-f(c_n)|  \\
&= \mu.
\end{aligned}$$

于是$\forall n\in\mathbb{N}$, $f(c_n)\le \mu$, $a\le c_n \le c_{n+1} < b$, 
故$\left\lbrace c_n\right\rbrace$单调递增有上界, 从而极限存在. 

<span style="display:block;text-align:right;">
$\square$
</span>


{: .remark}
> 把这个问题修改为如下: 
> 
> {: .problem}
> > $\color{blue}{\mathbf{\text{1a.}}}$ 设$f$是在$[a,+\infty)$中定义的函数, 且存在常数$L>0$, 使得
> > 
> > $$|f(x)-f(y)|\le L|x-y|, \qquad \forall x,y\in[a,+\infty).$$
> > 
> > 设$f(a) < \mu$, 并且存在$\xi\in[a,+\infty)$使得$f(\xi)=\mu$. 
> > 令$c_1=a$, 当$n\ge 1$时, $c_{n+1}=c_n+\dfrac{1}{L}[\mu-f(c_n)]$. 
> > 研究数列$\lbrace c_n\rbrace$是否收敛.
> 
> 你能否写出它的证明过程? 





{: .problem}
> $\color{blue}{\mathbf{\text{2.}}}$ 设$a_n>0$, 且数列$\left\lbrace\dfrac{a_{n+1}+a_{n+2}}{a_n}\right\rbrace$收敛于$\alpha$. 
> 若$\alpha>2$, 证明: 数列$\lbrace a_n\rbrace$没有上界. 


**证明：** 对于$\varepsilon = \dfrac{\alpha-2}{2}$, 存在正整数$N$, 使得当$n\ge N$时, 

$$\left|\dfrac{a_{n+1}+a_{n+2}}{a_n}-\alpha\right| < \varepsilon = \dfrac{\alpha-2}{2},$$

即

$$\dfrac{a_{n+1}+a_{n+2}}{a_n} > \dfrac{\alpha+2}{2}:= q > 2.$$

即

$$a_{n+1}+a_{n+2} > qa_n.$$ 

记$\lambda=\dfrac{-1-\sqrt{1+4q}}{2}$为方程$x^2+x-q=0$的根. 于是由上式可得

$$\begin{aligned}
a_{n+2} - \lambda a_{n+1}& > -(\lambda+1)a_{n+1}+qa_n \\
& = -(\lambda+1)\left(a_{n+1}-\dfrac{q}{\lambda+1}a_n\right) \\
& = -(\lambda+1)(a_{n+1}-\lambda a_n),
\end{aligned}$$

注意$-(\lambda+1)=\dfrac{\sqrt{1+4q}-1}{2} > 1$, 因此对$n=N,N+1,\cdots$累乘可得

$$a_{n+1}-\lambda a_n > \left(\dfrac{\sqrt{1+4q}-1}{2}\right)^{n-N}\underbrace{(a_{N+1}-\lambda a_N)}_{>0}.$$

所以让$n\to\infty$可得

$$\lim\limits_{n\to\infty}(a_{n+1}-\lambda a_n)=+\infty. \qquad (*)$$

(反证法)如果$\lbrace a_n\rbrace$是有上界的数列, 设$a_n \le M$, 则

$$a_{n+1}-\lambda a_n \le M+\dfrac{1+\sqrt{1+4q}}{2}M.$$

所以根据极限的保序性, 必有

$$\limsup\limits_{n\to\infty}(a_{n+1}-\lambda a_n) \le M+\dfrac{1+\sqrt{1+4q}}{2}M.$$

这与$(*)$矛盾. 
因此数列$\lbrace a_n\rbrace$没有上界. 

<span style="display:block;text-align:right;">
$\square$
</span>

{: .problem}
> $\color{blue}{\mathbf{\text{3.}}}$ 设函数$f$在区间$(0,1)$中处处都有定义, 且$f$在$(0,1)$中每一点处的极限均为零. 证明: 
> (i)$f$必有零点; (ii)$\lbrace x\in(0,1)|f(x)\ne 0\rbrace$至多可数.

**证明：【错解】** 取区间$[a_k,b_k]=\left[\dfrac{1}{k},1-\dfrac{1}{k}\right]\subset(0,1)$, 其中$k\in\mathbb{N}$是正整数. 

对任意$\varepsilon>0$, 对任意$x\in[a_k,b_k]$, 由条件, 存在$\delta_x>0$, 使得当$y\in V(x,\delta_x)$时, 
有$\vert f(y)\vert  < \varepsilon$. 

由于

$$[a_k,b_k]
=\bigcup\limits_{x\in [a_k,b_k]}(x-\delta_x, x+\delta_x),$$

则根据有限覆盖定理, 存在有限个点$x_1^{(k)},\cdots,x_{n_k}^{(k)}$满足

$$[a_k,b_k]=
\bigcup\limits_{i=1}^{n_k}\left(x_i^{(k)}-\delta_{i}^{(k)}, x_i^{(k)}+\delta_{i}^{(k)}\right).$$

于是, 在集合$A_k=[a_k,b_k]\setminus\lbrace x_1^{(k)},\cdots, x_{n_k}^{(k)}\rbrace$中, 有

$$|f(y)| < \varepsilon, \quad \forall y\in A_k.$$

所以由$\varepsilon$的任意性, 可知$f(y)=0$, $\forall y\in A_k$. 

然后, $(0,1)\subset\bigcup\limits_{k=1}^{\infty}\bigcup\limits_{i=1}^{n_k}\left(x_i^{(k)}-\delta_{i}^{(k)}, x_i^{(k)}+\delta_{i}^{(k)}\right)$,
所以$f$最多在可数个点非零. 

{: .remark }
> **错误原因：** $\varepsilon$改变的时候, $x_i^{(k)}$和$n_k$也会变. 



**证明：【正解】** 取区间$[a_k,b_k]=\left[\dfrac{1}{k},1-\dfrac{1}{k}\right]\subset(0,1)$, 其中$k\in\mathbb{N}$是正整数. 

对任意正整数$m$, 对任意$x\in[a_k,b_k]$, 由条件, 存在$\delta_x^{(m)}>0$, 使得当$y\in V(x,\delta_x^{(m)})$时, 
有$\vert f(y)\vert  < \dfrac{1}{m}$. 

由于

$$[a_k,b_k]
=\bigcup\limits_{x\in [a_k,b_k]}(x-\delta_x^{(m)}, x+\delta_x^{(m)}),$$

则根据有限覆盖定理, 存在有限个($n_{k,m}$个)点$x_1^{(k,m)},\cdots,x_{n_{k,m}}^{(k,m)}$满足

$$[a_k,b_k]=
\bigcup\limits_{i=1}^{n_{k,m}}\left(x_i^{(k,m)}-\delta_{i}^{(k,m)}, x_i^{(k,m)}+\delta_{i}^{(k,m)}\right).$$

于是, 在集合$A_{k,m}=[a_k,b_k]\setminus\lbrace x_1^{(k,m)},\cdots, x_{n_{k,m}}^{(k,m)}\rbrace$中, 有

$$|f(y)| < \dfrac{1}{m}, \quad \forall y\in A_{k,m}.$$

考虑集合$A_k=\bigcap\limits_{m=1}^{\infty} A_{k,m}$, 则$A_k\ne\varnothing$(因为$A_k$是$[a_k,b_k]$挖掉至多可数个点构成的集合),
并且满足

$$|f(y)|=0, \forall y\in A_k.$$

因此$f$存在零点. 

最后, $(0,1)\subset\bigcup\limits_{k=1}^{\infty}\bigcup\limits_{m=1}^{\infty}\bigcup\limits_{i=1}^{n_{k,m}}\left(x_i^{(k,m)}-\delta_{i}^{(k,m)}, x_i^{(k,m)}+\delta_{i}^{(k,m)}\right)$,
所以$f$的非零点至多是下面的点:

$$\bigcup\limits_{k=1}^{\infty}\bigcup\limits_{m=1}^{\infty}\bigcup\limits_{i=1}^{n_{k,m}}\{x_i^{(k,m)}\}.$$

所以$f$在至多可数个点非零. 

<span style="display:block;text-align:right;">
$\square$
</span>



{% endraw %}
