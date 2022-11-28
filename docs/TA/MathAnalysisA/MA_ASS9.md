---
layout: default
title: 第9次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 15
---

## 第9次作业

习题4.1/17(2)(4)(6), 19(2), 21.

习题4.2/2(1)(3), 3(1)(3), 5, 7(2), 9, 11, 13.

习题4.3/1,3,4(奇数), 5(奇数)

## 主要问题

计算的问题这里就不说了, 主要提一下4.2/13题. 拿到A而不是A+的同学基本上就是13题有问题.

### 4.1/17题

{: .problem}
> **问题：** 写$y'=u^{e^v}e^v\cdot\dfrac{uv'\ln u+e^vu'}{u}.$

错误原因：不要抄知乎上某位同学整理的答案. 发现大面积跟这份答案雷同的我都最多只给C, 如果你觉得不服气就加Fiddie微信. 


### 4.3/5(5)题

{: .note}
> 答案是$\dfrac{3}{8}\sqrt{2}-\dfrac{1}{8}\ln(1+\sqrt{2})$, 或者写$\dfrac{3}{8}\sqrt{2}-\dfrac{1}{16}\ln(3+2\sqrt{2})$,
> 或者写$\dfrac{3}{8}\sqrt{2}+\dfrac{\ln 2}{16}-\dfrac{\ln(2+\sqrt{2})}{8}$都对,
> 有些同学可能被我改错了, 不好意思.

### 4.3/7(2)题

{: .note}
> 事实上不需要证$\sin x < x$的部分, 例3.1.6已证. 而且从逻辑上看, 如果我们需要用到结论$(\sin x)'=\cos x$, 
> 那么就要用到结论$\lim\limits_{x\to 0}\dfrac{\sin x}{x}=1$, 但是证这个极限需要用$\sin x < x$. 





### 4.2/13题

本题的证明方法是先证$f$的左导数恒大于等于$0$时$f$单调递增, 然后推出$f$的左导数恒小于等于$0$时$f$单调递减.


{: .problem}
> **问题1：** 写$f'(x)$.

错误原因：题目条件没说$f$导数存在.

{: .problem}
> **问题2：** 由于$f'$左导数存在, 所以存在$\delta>0$, 当$x\in (b-\delta,b)$时$|f(x)-f(b)| < \varepsilon$.
> 然后利用$f$在$[a,b]$一致连续可知$f$在$[a,b]$上是常值函数. 

错误原因：并不能推出来吧. 

{: .problem}
> **问题3：** 没有利用连续的条件, 从$f(x)$在一个小区间上是常数直接推出整体是常数.

错误原因：也推不出来吧, 例如分段常值函数

$$f(x)=\left\{\begin{aligned}
&0, && x\in\left[0,\dfrac{1}{2}\right], \\
&1, &&x\in\left(\dfrac{1}{2},1\right],
\end{aligned}\right.$$

在任意一点的左导数都为$0$但并不是常数. 

{: .problem}
> **问题4：** 推出对任意$x\in(a,b]$存在$\delta>0$使得$f$在$[x-\delta,x]$上是常值函数,
> 然后用2.5/12题(局部常值函数是常值函数)推出$f$在$[a,b]$上是常值函数.

错误原因：一个函数$g$是局部常值函数指的是：对任意$x\in(a,b)$存在$\delta>0$使得$g$在$[x-\delta,x+\delta]$上是常值函数,
这里的$f$不满足局部常值函数定义.

{: .problem}
> **问题5：** 记左导数为$g(x)$, 写$g(x-\Delta x)=\lim\limits_{\Delta x\to 0^-}\dfrac{f(x-\Delta x+\Delta x)-f(x-\Delta x)}{\Delta x}.$

错误原因：这学过函数极限就一眼看出是错的吧. 正确的应该是

$$g(x-\Delta x)=\lim\limits_{\Delta y\to 0^-}\dfrac{f(x-\Delta x+\Delta y)-f(x-\Delta x)}{\Delta y}.$$

虽然这是正确的, 但这样写并不能证出任何东西. 

{: .problem}
> **问题6：** 根据$f(x)$在$x_0$处的左导数等于$0$可知存在$\delta>0$使得对任意$x\in(x_0-\delta,x_0)$有$f(x)=f(x_0)$.

错误原因：仅用在一点处左导数等于$0$不能推出在局部是常函数. 反例: $f(x)=x^2$在$x=0$处.

需要想办法把“左导数在区间内恒等于$0$”的条件用上. 

## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.** 设$\mathbf{I}_n$是$n\times n$单位矩阵, $\mathbf{A}$是$n\times n$实矩阵, 
函数$f(x)=\mathrm{det}(\mathbf{I}+x\mathbf{A})$. 计算$f'(0)$的值.

{: .note}
> Legendre多项式在数值计算方法(大二下学期和大三上学期的课)中经常用到. 感兴趣的同学欢迎以后走信息与计算科学方向.

**2.(Legendre多项式)** 考虑多项式函数

$$L_n(x)=\dfrac{1}{2^nn!}\dfrac{\mathrm{d}^n}{\mathrm{d}x^n}(x^2-1)^n, \qquad n\in\mathbb{N}.$$

(1)证明: 对任意$n\ge 1$, 有递推关系式

$$(n+1)L_{n+1}(x)=(2n+1)xL_n(x)-nL_{n-1}(x).$$

(2)求$\mathrm{deg}(L_n(x))$. 

(3)证明: 对任意次数不超过$n-1$次的多项式$P(x)$, 都有

$$\int_{-1}^1L_n(x)P(x)\mathrm{d}x=0.$$

从而推导出当$m\ne n$时, 多项式列$\lbrace L_n(x)\rbrace$满足如下的**正交性质**: 

$$\int_{-1}^1L_m(x)L_n(x)\mathrm{d}x=0.$$

(4)计算

$$\int_{-1}^1(L_n(x))^2\mathrm{d}x.$$

{: .note}
> 第三章(74页)我们证明了Young不等式: 
> 
> $$ab\le\dfrac{a^p}{p}+\dfrac{b^q}{q},$$ 
> 
> 其中$a>0, b>0, p>1, q>1$, 并且$p^{-1}+q^{-1}=1$. 
> 我们用积分来给出它的另外一种证明.

**3.** 设$y=f(x)$和$x=g(y)$互为相反数且都是非负、单调递增的可导函数, 
并且$f(0)=g(0)=0$. 证明: 当$x,y\ge 0$时, 

$$xy\le \int_0^xf(t)\mathrm{d}t+\int_0^yg(t)\mathrm{d}t.$$

然后导出Young不等式

$$xy\le\dfrac{1}{p}x^p+\dfrac{1}{q}x^q,$$

其中, $x,y\ge 0$, $p,q>1$满足$p^{-1}+q^{-1}=1$. 

上述不等式等号成立条件是什么？它对应着什么几何意义? 


{: .remark}
> 把“可导”的条件减弱为“连续”, 甚至把“连续”的条件去掉也对, 但是应该是要用到第六章的知识才能证. 
>
> 可以参考[https://handwiki.org/wiki/Integral_of_inverse_functions](https://handwiki.org/wiki/Integral_of_inverse_functions).



&nbsp; 

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## 思考题提示

**1.** 答案为$\mathrm{tr}(\mathbf{A})$. 

**2.** (1)用Leibniz公式; (3)分部积分$n$次. 
(4)分部积分$n$次, 最后可能要用到Wallis公式, 答案为$\dfrac{2}{2n+1}$. 

**3.** 由恒等式$g(f(x))=x$, 两边同乘$f'(x)$可得$f'(x)g(f(x))=xf'(x)$, 两边作积分.