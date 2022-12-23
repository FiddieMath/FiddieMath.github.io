---
layout: default
title: 第12次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 22
---

# 问卷填写

《数学分析》助教个人主页已经陪伴同学们多时，希望同学们可以填写一下这份问卷，反馈一下使用情况，谢谢！

**(根据填写情况可以加Fiddie微信获得红包)**


<div align = center>
<img src="/pics/wjx.png" width = "300"/>
</div>

# 第12次作业

**一、** 设$h>0$, 并且$f$在$[a-h,a+h]$上连续, 在$(a-h,a+h)$上可导, 证明: 存在$\theta\in(0,1)$满足

$$\dfrac{f(a+h)-2f(a)+f(a-h)}{h}=f'(a+\theta h)-f'(a-\theta h).$$

**二、** 假设函数$f$在$(0,a]$连续, 在$(0,a)$可导, 并且极限$\lim\limits_{x\to 0^+}\sqrt{x}f'(x)$存在,
证明: $f$在$(0,a]$一致连续.

**三、** 假设$f$是区间$I$上的凸函数并且$f$二阶可导, 证明$e^f$也是$I$上的凸函数.
如果$f$是凸函数, 但未必可导呢? 如果仍成立请给出证明, 如果不成立请举出反例.

**四、** 假设$f$在区间$(a,b)$上有定义, 并且对任何$x_0\in(a,b)$都存在$\mu\in\mathbb{R}$(依赖于$x_0$)使得

$$f(x)\ge f(x_0)+\mu(x-x_0), \qquad \forall x\in(a,b),$$

证明$f$是$(a,b)$上的凸函数.

**五、** 判断下面两个数的大小并给出证明:

$$\int_0^1e^{\arctan x}\mathrm{d}x, \qquad \sqrt{\dfrac{e}{2}}.$$

**六、** 计算极限: 

|(1)$\lim\limits_{x\to 0}\left(\dfrac{1}{\sin x}-\dfrac{1}{x}\right)$; | (2)$\lim\limits_{x\to 1}\dfrac{\ln\cos(x-1)}{1-\sin\frac{\pi x}{2}}$; | (3)$\lim\limits_{x\to 1}\dfrac{x-x^2}{1-x+\ln x}$; |
|(4)$\lim\limits_{x\to 0}(\tan x)^{\sin x}$; | (5)$\lim\limits_{x\to 0}(\cos \pi x)^{\frac{1}{x^2}}$; | (6)$\lim\limits_{x\to+\infty}x(3^{\frac{1}{x}}-2^{\frac{1}{x}})$; |
|(7)$\lim\limits_{x\to+\infty}\left(\dfrac{\ln(1+x)}{x}\right)^{\frac{1}{x}}$; |(8)$\lim\limits_{x\to+\infty}\left(\dfrac{\pi}{2}-\arctan x\right)^{\frac{1}{x}}$; |(9)$\lim\limits_{x\to 0}\left(\dfrac{(1+x)^{\frac{1}{x}}}{e}\right)^{\frac{1}{x}}$. |

**七、** 假设$x\in[-1,1]$.

(1)证明：存在$\theta\in(0,1)$(依赖于$x$)使得$\arcsin x=\dfrac{x}{\sqrt{1-\theta^2x^2}}$;

(2)计算极限$\lim\limits_{x\to 0}\theta$.

**八、** 假设$f$在$0$附近二阶可导并且$\lim\limits_{x\to 0}\left(\dfrac{\sin 3x}{x^3}+\dfrac{f(x)}{x^2}\right)=0$.

(1)求$f(0)$, $f'(0)$, $f^{\prime\prime}(0)$;

(2)计算极限$\lim\limits_{x\to 0}\left(\dfrac{3}{x^2}+\dfrac{f(x)}{x^2}\right)$. 

# 主要问题

## 第二题

{: .problem}
> $(1)$ $\sqrt{x}f'(x)$在$(0,a]$上连续/有界

错误原因：已知条件无法保证这件事，已知条件只能保证该函数在$0$的一个小邻域内有界

{: .problem}
> $(2)$ 记$\lim_{x\to 0^{+}}\sqrt{x}f'(x)=\alpha$ ,由L'hôpital法则$\lim_{x\to 0^+}\frac{f(x)}{2\sqrt{x}}=\lim_{x\to 0^+}\sqrt{x}f'(x)=\alpha$由$\lim_{x\to 0^+}2\sqrt{x}=0$有$\lim_{x\to 0^+}f(x)=0$

错误原因：L'hôpital法则不能这样倒着用，不信你把$f(x)$加一个常数是不是该有的都还有？

## 第四题

{: .problem}
> $(1)$只证明了该函数在区间上具有中点凸性就认为说明了凸性

错误原因：见命题$5.3.6$,他是有条件的

{: .problem}
> $(2)$ 对$f$求导

错误原因：条件里并没有说$f$可导

## 第五题

{: .problem}
> $(1)$在某点处Taylor展开后在整个区间做积分当作近似值

错误原因：是不得分析一下误差？

## 第八题

{: .problem}
> $(1)$对$f$求了三阶导

错误原因：条件里只说$f$二阶可导



## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.(L'Hospital法则的反例)** 设$f(x)=x^2\sin\dfrac{1}{x}, g(x)=x$. 证明: 

$$\lim\limits_{x\to 0}\dfrac{f(x)}{g(x)}=0,$$

但是极限$\lim\limits_{x\to 0}\dfrac{f'(x)}{g'(x)}$不存在. 

&nbsp; 

&nbsp; 

{: .note}
> 设$I$是个区间, 称一个函数$f:I\to\mathbb{R}$是**对数凸的(log-convex)**, 
> 若对于任意的非负实数$\lambda_1,\lambda_2$, $\lambda_1+\lambda_2=1$, 
> 以及$x_1,x_2\in\mathbb{R}$, 有
> 
> $$\ln f(\lambda_1x_1+\lambda_2x_2) \le \lambda_1\ln f(x_1)+\lambda_2\ln f(x_2).$$
>
> 这个定义出自Boyd-Vandenburghe的《凸优化》, 如果同学们以后有志于从事优化理论、机器学习等方面的研究,
> 凸优化是必须要学的, 一般来说人工智能学院会在大二开设这门课, 需要一定的多元微积分基础.

**2.** 已知二元函数$f:\mathbb{R}\times [c,d]\to\mathbb{R}^+$. 
若$f(x,y)$关于$x$分量是对数凸的, 
证明: 函数$\displaystyle g(x)=\int_c^df(x,y)\mathrm{d}y$也是对数凸的. 

&nbsp; 

&nbsp; 

**3.** 设$f:\mathbb{R}\to\mathbb{R}$处处有三阶导数, 证明存在$\xi\in\mathbb{R}$, 使得

$$f(\xi)f'(\xi)f''(\xi)f'''(\xi)\ge 0.$$

&nbsp; 

&nbsp; 

**4.** 设$f:\mathbb{R}\to\mathbb{R}$是无穷次可微函数, 并且

$$f\left(\dfrac{1}{n}\right)=\dfrac{n^2}{n^2+1}, \forall n=1,2,3,\cdots.$$

对任意正整数$k$, 求$f^{(k)}(0)$的值. 

&nbsp; 

&nbsp; 

{: .note}
> **Poincaré(庞加莱)不等式**在偏微分方程、有限元方法(我的研究方向!)中会用到. 下面的Poincaré不等式是一维情形. 
> 对于更一般的情形, 同学们以后接触**Sobolev空间**的概念时会学到. 
>
> 我们并不要求常数$C$尽可能小(即得到的不等式尽可能sharp), 因为在偏微分方程的理论研究中, 
> 这种与函数无关的常数都是用一个字母$C$来代替的, 只要存在这样的$C$就足够了. 

**5.** 设$p,q\in[1,+\infty)$, $a,b\in\mathbb{R}$, $a < b$. 

(1)设$f$是$[a,b]$中的可微函数, 
证明存在常数$C$(依赖于$p,q,a,b$, 但与$f$无关), 使得

$$\left(\int_a^b\left|f(x)-\dfrac{1}{b-a}\int_a^bf(t)\mathrm{d}t\right|^q\mathrm{d}x\right)^{\frac{1}{q}}
\le C\left(\int_a^b|f'(x)|^p\mathrm{d}x\right)^{\frac{1}{p}}.$$

(2)设$f$是$[a,b]$中的可微函数, 满足$f(a)=f(b)=0$. 
证明存在常数$C$(依赖于$p,q,a,b$, 但与$f$无关), 使得

$$\left(\int_a^b |f(x)|^q\mathrm{d}x\right)^{\frac{1}{q}}
\le C\left(\int_a^b|f'(x)|^p\mathrm{d}x\right)^{\frac{1}{p}}.$$

(3)设$f\in C^n[a,b]$, $f^{(k)}(a)=f^{(k)}(b)=0, k=0,1,\cdots,n-1$. 
证明存在常数$C$(依赖于$p,q,a,b$, 但与$f$无关), 使得

$$\left(\int_a^b |f(x)|^q\mathrm{d}x\right)^{\frac{1}{q}}
\le C\left(\int_a^b|f^{(n)}(x)|^p\mathrm{d}x\right)^{\frac{1}{p}}.$$

&nbsp; 

&nbsp; 


{: .note}
> 在第三章(74页)和[第9次作业的助教思考题](/docs/TA/MathAnalysisA/MA_ASS9/)中我们证明了Young不等式: 
> 
> $$ab\le\dfrac{a^p}{p}+\dfrac{b^q}{q},$$ 
> 
> 其中$a>0, b>0, p>1, q>1$, 并且$p^{-1}+q^{-1}=1$. 
> 下面我们来研究它的一个一般情况, 这个一般情况在变分法、理论力学中会用到. 

**6.** 定义在区间$I\subset\mathbb{R}$上的函数$f:I\to\mathbb{R}$的**Legendre变换** 是函数

$$f^*(t)=\sup\limits_{x\in I}(tx-f(x)).$$

证明: 

(1)使得$f^{\ast}(t)\in\mathbb{R}$(即$f^{\ast}(t)\ne\infty$)的值$t\in\mathbb{R}$构成的集合$I^*$
可能是空集、单点集或者区间. 而如果$I^{\ast}$是区间, 则函数$f^{\ast}(t)$在$I^{\ast}$上是凸函数. 

(2)若$f$是凸函数, 则$I^{\ast}\ne\varnothing$且当$f^{\ast}\in C^0(I^{\ast})$时, 

$$(f^{\ast})^{\ast}(x)=\sup\limits_{t\in I^{\ast}}(xt-f^{\ast}(t))=f(x)$$

对任意的$x\in I$成立. 也就是说, 凸函数的Legendre变换是**对合变换**.
(一个变换$\mathcal{F}$是对合变换指的是$\mathcal{F}^2=I$, 其中$I$表示恒等变换.)

(3)当$x\in I$, $t\in I^*$时, 有如下Young不等式的推广版本: 

$$xt\le f(x)+f^{\ast}(t).$$

(4)当$f$是凸的可微函数时, $f^{\ast}(t)=tx_t-f(x_t)$, 其中$x_t$由方程

$$t=f'(x)$$

确定; 由此得到Legendre变换$f^{\ast}$及其自变量$t$的几何解释, 它表明Legendre变换是一个在函数$f$图像的切线集合上定义的函数.

(5)当$\alpha>1$且$x\ge 0$时, 函数$f(x)=\dfrac{1}{p}x^p$的Legendre变换是函数$f^{\ast}(t)=\dfrac{1}{q}t^q$,
其中$t\ge 0$且$p^{-1}+q^{-1}=1$. 于是由(3)可知有Young不等式

$$xt\le\dfrac{1}{p}x^p+\dfrac{1}{q}x^q.$$

(6)函数$f(x)=e^x$的Legendre变换是函数$f^{\ast}(t)=t\ln\dfrac{t}{e}$, $t>0$, 并且满足不等式

$$xt\le e^x+t\ln\dfrac{t}{e}, \forall x\in\mathbb{R}, t>0.$$




&nbsp;

&nbsp; 

&nbsp;

&nbsp; 

&nbsp;

&nbsp; 

&nbsp;

&nbsp;

&nbsp; 

&nbsp;

&nbsp; 

&nbsp;

&nbsp; 

&nbsp;

## 提示（实在不会做再去看提示！）

**2.** 用Holder不等式和凸函数定义.

**3.** 先用介值定理和Darboux定理讨论$f,f^{\prime},f^{\prime\prime},f^{\prime\prime\prime}$之一存在正或负的情形.
再考虑$f,f^{\prime},f^{\prime\prime},f^{\prime\prime\prime}$是恒正或恒负的情形, 证明$f,f^{\prime\prime}$符号相同, $f^{\prime},f^{\prime\prime\prime}$符号相同.

**4.** 函数$f(x)=\dfrac{1}{1+x^2}$满足题目要求. 假设$g(x)$也满足题目要求, 考虑函数$h(x)=f(x)-g(x)$的各阶导数.

**5.** 考虑$f(x)-f(t)=\int_t^xf'(s)\mathrm{d}s$, 然后用Holder不等式. 

&nbsp;

&nbsp; 

&nbsp;

&nbsp; 

&nbsp;

&nbsp; 

&nbsp;

&nbsp;

&nbsp; 

&nbsp;

## 部分解答(看了提示也不会再去看答案！)

**2.** [https://www.zhihu.com/question/567657207/answer/2767096429](https://www.zhihu.com/question/567657207/answer/2767096429)

如果$f(x,y)$关于$x$是log-convex的，

$$\ln f(ax_1+bx_2, y)\le a \ln f(x_1,y)+b\ln f(x_2,y)$$

其中$a+b=1$, $a,b\ge 0$, $x_1,x_2\in\mathbb{R}$, 
因此，根据Holder不等式，

$$\begin{aligned} 
&\quad \ln g(ax_1+bx_2,y) \\ 
&=\ln \int_Cf(ax_1+bx_2,y)\mathrm{d}y \\ 
&\le \ln \int_Cf(x_1,y)^af(x_2,y)^b\mathrm{d}y \\ 
&\le \ln\left[\left(\int_C[f(x_1,y)^a]^{\frac{1}{a}}\mathrm{d}y\right)^{a} 
\left(\int_C[f(x_2,y)^b]^{\frac{1}{b}}\mathrm{d}y\right)^{b}\right] \\ 
&=a\ln\int_Cf(x_1,y)\mathrm{d}y+b\ln\int_Cf(x_2,y)\mathrm{d}y \\ 
&=a\ln g(x_1,y) + b\ln g(x_2,y). 
\end{aligned}$$

这就完成了证明.


{: .remark}
> 下面这题出自1998Putnam.

**3.** 若$f,f^{\prime},f^{\prime\prime},f^{\prime\prime\prime}$其中之一有正有负, 根据介值定理或者Darboux定理, 存在$\xi\in\mathbb{R}$,
使得$f(\xi)f^{\prime}(\xi)f^{\prime\prime}(\xi)f^{\prime\prime\prime}(\xi)=0$, 结论成立. 

下面证明, 若$f,f^{\prime},f^{\prime\prime}$都是恒正或恒负, 则$f,f^{\prime\prime}$符号相同. 不妨设$f^{\prime\prime}$恒正. 则由Taylor展开, 

$$f(x)=f(0)+f^{\prime}(0)x+\dfrac{f^{\prime\prime}(c)x^2}{2}, \exists c\text{介于}0,x\text{之间}, $$

所以对任意$x$, 有$f(x)>f(0)+f^{\prime}(0)x$. 若$f^{\prime}(0)>0$, 则当$x$是充分大的正数时, $f(x)$是正的.
若$f^{\prime}(0) < 0$, 则当$x$是充分大的负数时, $f(x)$是正的. 因此$f(x)$恒正.

类似地, 若$f^{\prime\prime}$恒负, 则$f$恒负, 因此$f(x)f^{\prime\prime}(x)\ge 0$对任意$x$都成立. 类似地可以证明, $f^{\prime}(x)f^{\prime\prime\prime}(x)\ge 0$对任意$x$都成立.

{: .remark}
> 下面这题出自1992Putnam.

**4.** 奇数次导数是$0$, 偶数次导数是$f^{(2n)}(0)=(-1)^n$.

显然, $f(x)=\dfrac{1}{1+x^2}$是符合题目要求的函数, 它的Taylor展开是

$$f(x)=1-x^2+x^4-\cdots,$$

于是$f^{(2n-1)}(0)=0$, $f^{(2n)}(0)=(-1)^n$. 假设$g(x)$是另外满足题目条件的函数, 
我们令$h(x)=f(x)-g(x)$, 则$h$是无穷次可微函数, 并且满足$h\left(\dfrac{1}{n}\right)=0$.
我们用反证法证明$h^{(k)}(0)=0(k=1,2,\cdots)$, 要不然, 取$k$是最小的正整数使得$h^{(k)}(0)\ne 0$, 
于是存在$\varepsilon>0$, 使得$h^{(k)}(0)$在区间$[0,\varepsilon)$上非零(为什么? )

取充分大的$n$使得$\dfrac{1}{n} < \varepsilon$. 于是, 利用Taylor展开可得

$$h\left(\dfrac{1}{n}\right)=\dfrac{h^{(k)}(\xi)}{k!},$$

其中$\xi < 1/n < \varepsilon$. 但是, 上式左边为$0$, 右边不为$0$, 产生矛盾. 

**5.** 设$\dfrac{1}{p}+\dfrac{1}{p'}=1$. 

(1)只需要注意到

$$\begin{aligned}
\mathrm{LHS}&=\left(\int_a^b\left|\dfrac{1}{b-a}\int_a^b\int_t^xf'(s)\mathrm{d}s\mathrm{d}t\right|^q\mathrm{d}x\right)^{\frac{1}{q}} \\
&\le \left(\int_a^b\left(\dfrac{1}{b-a}\int_a^b\left|\int_t^xf'(s)\mathrm{d}s\right|\mathrm{d}t\right)^q\mathrm{d}x\right)^{\frac{1}{q}} \\
&\le \left(\int_a^b\left(\dfrac{1}{b-a}\int_a^b\int_a^b|f'(s)|\mathrm{d}s\mathrm{d}t\right)^q\mathrm{d}x\right)^{\frac{1}{q}} \\
&= (b-a)^{\frac{1}{q}}\left[\int_a^b|f'(s)|\mathrm{d}s\right]^q \\
&\le (b-a)^{\frac{1}{q}}\left[\left(\int_a^b|f'(s)|^p\mathrm{d}s\right)^{\frac{1}{p}}\left(\int_a^b1^{p'}\mathrm{d}s\right)^{\frac{1}{p'}}\right] \\
&=(b-a)^{1-\frac{1}{p}+\frac{1}{q}}\left(\int_a^b|f'(s)|^p\mathrm{d}s\right)^{\frac{1}{p}}. 
\end{aligned}$$

(2)只需要注意到

$$\begin{aligned}
\mathrm{LHS}&=\left(\int_a^b\left|\int_a^xf'(t)\mathrm{d}t\right|^q\mathrm{d}x\right)^{\frac{1}{q}} \\
&\le \left(\int_a^b\left(\int_a^b|f'(t)|\mathrm{d}t\right)^q\mathrm{d}x\right)^{\frac{1}{q}} \\
& = (b-a)^{\frac{1}{q}}\int_a^b|f'(t)|\mathrm{d}t \\
&\le (b-a)^{\frac{1}{q}}\left(\int_a^b|f'(t)|^p\mathrm{d}t\right)^{\frac{1}{p}}\left(\int_a^b1^{p'}\mathrm{d}t\right)^{\frac{1}{p}} \\
& = (b-a)^{1-\frac{1}{p}+\frac{1}{q}}\left(\int_a^b|f'(t)|^p\mathrm{d}t\right)^{\frac{1}{p}}.
\end{aligned}$$

(3)由(2)的证明过程,

$$\begin{aligned}
\left(\int_a^b|f(x)|^q\mathrm{d}x\right)^{\frac{1}{q}}
&\le (b-a)^{\frac{1}{q}}\int_a^b|f'(t)|\mathrm{d}t.
\end{aligned} \tag{5.1}$$

对上式取$q=1$, 于是对任意可微函数$g$都有

$$\begin{aligned}
\int_a^b|g(x)|\mathrm{d}x
&\le (b-a)\int_a^b|g'(t)|\mathrm{d}t.
\end{aligned} \tag{5.2}$$

因此, 结合$(5.1)$, 并在$(5.2)$中让$g$为$f',f^{\prime\prime},\cdots,f^{(n-1)}$, 可得

$$\begin{aligned}
\left(\int_a^b|f(x)|^q\mathrm{d}x\right)^{\frac{1}{q}}
&\le (b-a)^{\frac{1}{q}}\int_a^b|f'(t)|\mathrm{d}t \\
&\le (b-a)^{1+\frac{1}{q}}\int_a^b|f''(t)|\mathrm{d}t \\
&\le (b-a)^{2+\frac{1}{q}}\int_a^b|f'''(t)|\mathrm{d}t \\
&\le\cdots\le(b-a)^{n-1+\frac{1}{q}}\int_a^b|f^{(n)}(t)|\mathrm{d}t  \\
&\le (b-a)^{n-1+\frac{1}{q}}\left(\int_a^b|f^{(n)}(t)|^p\mathrm{d}t\right)^{\frac{1}{p}} \left(\int_a^b1^{p'}\mathrm{d}t\right)^{\frac{1}{p'}} \\
& = (b-a)^{n-\frac{1}{p}+\frac{1}{q}}\left(\int_a^b|f^{(n)}(t)|^p\mathrm{d}t\right).
\end{aligned} $$


