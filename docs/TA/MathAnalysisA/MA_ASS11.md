---
layout: default
title: 第11次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 20
---

# 问卷填写

《数学分析》助教个人主页已经陪伴同学们多时，希望同学们可以填写一下这份问卷，反馈一下使用情况，谢谢！

**(根据填写情况可以加Fiddie微信获得红包)**


<div align = center>
<img src="/pics/wjx.png" width = "300"/>
</div>

# 第11次作业

**一、**考虑积分

$$I_n=\int_1^{1+\frac{1}{n}}\sqrt{1+x^n}\mathrm{d}x,$$

(1)证明$\lim\limits_{n\to\infty}I_n=0$;

(2)证明$nI_n$有极限, 并计算该极限(极限的值不必精确算出来, 可用积分表示).

**二、**假设$f\in C^0[A,B]$, $A < a < b < B$. 证明:

$$\lim\limits_{h\to 0}\int_a^b\dfrac{f(x+h)-f(x)}{h}\mathrm{d}x=f(b)-f(a).$$

**三、**假设$f\in C^0(\mathbb{R})$是以$T>0$为周期的周期函数, 证明:

$$\lim\limits_{x\to+\infty}\dfrac{1}{x}\int_0^xf(t)\mathrm{d}t=\dfrac{1}{T}\int_0^Tf(t)\mathrm{d}t.$$

**四、**假设$f$定义在$[a,b]$上, 满足：存在$L>0$和$\delta>0$使得

$$|f(x)-f(y)|\le L|x-y|^{1+\delta}.$$

证明: $f$一定是常值函数.

**五、**求函数的最大值和最小值:

(1)$f(x)=x^2\sqrt{1-x^2}, x\in[0,1]$;

(2)$f(x)=x^2e^{-x}, x\ge 0$.

**六、**考虑函数

$$f(x)=\left\{\begin{aligned}
&x+2x^2\sin\frac{1}{x}, &&x\ne 0, \\
&0, &&x=0.
\end{aligned}\right.$$

是否存在$\delta>0$使得$f$在$(-\delta,\delta)$上单调递增？为什么？

**七、**证明Hermite多项式

$$H_n(x)=\dfrac{(-1)^n}{n!}e^{\frac{x^2}{2}}\dfrac{\mathrm{d}^n}{\mathrm{d}x^n}(e^{-\frac{x^2}{2}})$$

有$n$个不同零点$(n\ge 1)$.

**八、**假设$f\in C^0[a,b]$, 证明: $f(x)$是$[a,b]$上的Lipschitz函数当且仅当$e^{f(x)}$是$[a,b]$上的Lipschitz函数.

**九、**假设$f(x)$在$(a,b)$可导, 且$f'(x)$在$(a,b)$上单调. 证明: $f'(x)$在$(a,b)$上连续.

# 主要问题


<span style="display:block;color:red;"> 
说明：有些同学的步骤是有错的, 但助教可能因为改得太快没改出来. 
同学们可以重新看一下自己的作业对照一下是不是有错. 
</span>


## 第一题

本题正确答案是

$$\int_0^1\sqrt{1+e^x}\mathrm{d}x=\int_1^e\dfrac{\sqrt{1+t}}{t}\mathrm{d}t=2(\sqrt{1+e}-\sqrt{2})+2\ln\dfrac{\sqrt{1+e}-1}{\sqrt{2}-1}-1.$$

{: .problem}
> **问题1：** 积分和极限是否可交换的问题.

我们还没学过积分和极限在什么情况下可交换, 所以类似于

$$\lim\limits_{n\to\infty}\int_{a_n}^{b_n}f_n(x)\mathrm{d}x
= \int_a^b\lim\limits_{n\to\infty}f_n(x)\mathrm{d}x$$

的结果都是错的.  (这里$a_n\to a$, $b_n\to b$)

{: .warning-title}
> 错误的例子
>
> ${\color{red}{1.}}$
> $\displaystyle\lim\limits_{n\to\infty}\int_1^{(1+\frac{1}{n})^n}\dfrac{t^{\frac{1-n}{n}}}{2\sqrt{1+t}}\mathrm{d}t
=\int_1^e\dfrac{\mathrm{d}t}{2t\sqrt{1+t}}.$
>
> ${\color{red}{2.}}$
> $\displaystyle\lim\limits_{n\to\infty}\int_1^{(1+\frac{1}{n})^n}\dfrac{\sqrt{1+t}}{t}\cdot t^{\frac{1}{n}}\mathrm{d}t
=\int_1^e\dfrac{\sqrt{1+t}\mathrm{d}t}{t}.$
>
> ${\color{red}{3.}}$
> $\displaystyle\lim\limits_{n\to\infty}\int_{\sqrt{2}}^{\sqrt{1+(1+\frac{1}{n})^n}}\dfrac{2u^2}{u^2-1}\cdot (u^2-1)^{\frac{1}{n}}\mathrm{d}u
=\int_{\sqrt{2}}^{\sqrt{1+e}}\dfrac{2u^2}{u^2-1}\mathrm{d}t.$

正确的做法是把$\int_{a_n}^{b_n}f_n(x)\mathrm{d}x$看成关于$n$的数列, 利用数列放缩和夹逼准则来求极限, 
即找与$x$无关的$u_n,v_n$以及$g(x),h(x)$使得

$$u_n\int_{a_n}^{b_n}g(x)\mathrm{d}x \int_a^bf_n(x)\mathrm{d}x\le v_n\int_{a_n}^{b_n}h(x)\mathrm{d}x,$$

然后不等号两边看成数列, 对两边求$n\to\infty$数列极限, 
从而得到$\lim\limits_{n\to\infty}\int_a^bf_n(x)\mathrm{d}x$的值.

{: .new-title}
> 正确的例子
>
> $\displaystyle\lim\limits_{n\to\infty}\int_1^{(1+\frac{1}{n})^n}\dfrac{\sqrt{1+t}}{t}\mathrm{d}t
=\int_1^e\dfrac{\sqrt{1+t}\mathrm{d}t}{t}.$

{: .problem}
> **问题2：** 取极限时取一半不取一半的问题.

下面的写法是错的：

{: .warning-title}
> 错误的例子
>
> ${\color{red}{1.}}$
> $\displaystyle\lim\limits_{n\to\infty}\int_n^{n+1}\sqrt{1+\left(\dfrac{x-n}{n}+1\right)}\mathrm{d}x
=\lim\limits_{n\to\infty}\int_n^{n+1}\sqrt{1+e^{x-n}}\mathrm{d}x.$
>
> ${\color{red}{2.}}$
> 写$f_n(x)=\sqrt{1+x^n}$, 由积分中值定理, 存在$\xi_n\in[1,1+1/n]$使得$I_n=\dfrac{1}{n}f_n(\xi_n)$. 
>
> $$\lim\limits_{n\to\infty}nI_n=\lim\limits_{n\to\infty}f_n(\xi_n)=\lim\limits_{n\to\infty}f_n(1)=\sqrt{2}.$$
> 
> ${\color{red}{3.}}$
> $\displaystyle\int_1^{1+\frac{1}{n}}\dfrac{n}{\sqrt{1+x^n}+x^{\frac{n}{2}}} \to x^{-\frac{n}{2}+1}\Big|_1^{1+\frac{1}{n}}.$
> 
> ${\color{red}{4.}}$
> $\displaystyle \lim\limits_{n\to\infty}n\int_0^{\frac{1}{n}}\sqrt{1+\left(\dfrac{1}{n}+1\right)^n}\mathrm{d}x
=\lim\limits_{n\to\infty}n\int_0^{\frac{1}{n}}\sqrt{1+e}\mathrm{d}x.$
> 
> ${\color{red}{5.}}$
> 设$F(t)=\int_1^t\sqrt{1+x^n}\mathrm{d}x$, 则$\lim\limits_{n\to\infty}I_n=\lim\limits_{t\to 1^+}F(t)=F(1).$

其中第3个例子莫名其妙, 原函数也没求对. 第5个例子的记号就有问题, 当涉及到含参数的函数时, 应该要写

$$F_n(t)=\int_1^t\sqrt{1+x^n}\mathrm{d}x.$$

这是因为表达式$\int_1^t\sqrt{1+x^n}\mathrm{d}x$同时和$n$与$t$有关. 

(事实上, 写$\lim\limits_{n\to\infty}F_n(1+1/n) = \lim\limits_{n\to\infty}F_n(1)$也犯了同样的错误. )

{: .problem}
> **问题3：** 用单调有界原理来克服“积分和极限可交换”的问题.

单调有界原理只是用来证明极限存在, 并不能用来算极限.

{: .problem}
> **问题4：** 消失的$\lim$. 

错误原因：写着写着就把$\lim$丢掉了. 

{: .warning-title}
> 错误的例子
>
> ${\color{red}{1.}}$
> $\displaystyle \lim\limits_{m\to\infty}\sum_{i=1}^m\sqrt{1+\left[\left(1+\dfrac{i}{m}\dfrac{1}{n}\right)^{n\cdot\frac{m}{i}}\right]^{\frac{i}{m}}}(x_i-x_{i-1})
= \lim\limits_{m\to\infty} \sum_{i=1}^m\sqrt{1+e^{\frac{i}{m}}}(x_i-x_{i-1}).$

第1个例子中就算加了$n\to\infty$也还是错, 需要保证$m\to\infty$和$n\to\infty$两个极限过程可交换,
但现在还没学到这, 见第8章. 

{: .problem}
> **问题5：** 用洛必达法则求极限
>
> $$\begin{aligned}
\lim\limits_{n\to\infty}nI_n
&=\lim\limits_{n\to\infty}\dfrac{\int_1^{1+1/n}\sqrt{1+x^n}\mathrm{d}x}{\frac{1}{n}} \\
&=\lim\limits_{n\to\infty}\dfrac{-\frac{1}{n^2}\sqrt{1+(1+\frac{1}{n})^n}}{-\frac{1}{n^2}}.
\end{aligned}$$

错误原因：首先洛必达法则是后面的知识，不要用没讲到的知识.

其次, 这是想对$n$求导? 
这里被积函数也包含$n$, 涉及到含参变量积分的导数, 是很后面的知识, 参见第15章. (很遗憾这里求错了)

涉及到数列极限可以尝试用Stolz公式(虽然我也不知道能不能做得出来).





## 第二题

本题的一个正确做法是设$F(x)=\int_a^xf(t)\mathrm{d}t$, 则$F$可导, 
然后把本题变成与$F(x)$有关的极限.

{: .problem}
> **问题1：** 题目有说$f$可导吗？以及积分和极限是否可交换的问题. 

{: .warning-title}
> 错误的例子
>
> ${\color{red}{1.}}$ 由Lagrange中值定理, 存在$\xi$介于$x$和$x+h$使得$\dfrac{f(x+h)-f(x)}{h}=f'(\xi),$
> 于是
> 
> $$\lim\limits_{h\to 0}\int_a^bf'(\xi)\mathrm{d}x = \int_a^bf'(x)\mathrm{d}x.$$
>
> ${\color{red}{2.}}$ 由于$\lim\limits_{h\to 0}\dfrac{f(x+h)-f(x)}{h}=f'(x)$, 
> 所以
> 
> $$\lim\limits_{h\to 0}\int_a^b\dfrac{f(x+h)-f(x)}{h}\mathrm{d}x=\int_a^bf'(x)\mathrm{d}x=f(b)-f(a).$$ 

首先, 题目没说$f$可导，出现$f'$都算错. 

其次, 即使$f$可导, 这里跟第一题一样涉及到积分和极限顺序是否可交换的问题, 
如果你写出了这个等式, 但没给出这个等式的严谨证明, 都算作错.

{: .problem}
> **问题2：** 写
>
> $$\begin{aligned}
&\quad \lim\limits_{h\to 0}\int_a^b\dfrac{f(x+h)-f(x)}{h}\mathrm{d}x \qquad\text{(令$n=\dfrac{b-a}{h}$)} \\
&=\lim_{h\to 0} \sum\limits_{i=1}^{\frac{b-a}{h}}\dfrac{f(a+hi)-f(a+h(i-1))}{h} h
\end{aligned}$$

**错误原因：** 想用积分的定义只能这样写: 

$$\begin{aligned}
&\quad \lim\limits_{h\to 0}\int_a^b\dfrac{f(x+h)-f(x)}{h}\mathrm{d}x \qquad\text{(令$d=\dfrac{b-a}{n}$)} \\
&=\lim_{h\to 0}\lim\limits_{n\to\infty} \sum\limits_{i=0}^{n}\dfrac{f(a+di+h)-f(a+di)}{h} d.
\end{aligned}$$

但这就涉及到两个极限的可交换性了，还没学到. 

{: .problem}
> **问题3：** 把积分中值定理写成微分中值定理. 

## 第三题

{: .problem}
> **问题1：** 设$y$为大于等于$0$且小于$T$的任意数, 则
>
> $$\lim\limits_{x\to+\infty}\dfrac{1}{x}\int_0^xf(t)\mathrm{d}t = \lim\limits_{n\to\infty}\dfrac{1}{nT+y}\int_0^{nT+y}f(t)\mathrm{d}t.$$

错误原因：需要先证明$\displaystyle \dfrac{1}{x}\int_0^xf(t)\mathrm{d}t$极限是否存在,
才能在$\displaystyle \dfrac{1}{x}\int_0^xf(t)\mathrm{d}t$前面加$\lim$. 

除此之外, 就算等号右边极限存在, 一般情况下($f$不连续的时候)并不能说明左边极限存在. 
把右边看成$n$的数列极限, 它只是一个子列的极限, 不一定等于左边函数的极限. 

{: .problem}
> **问题2：** 写
>
> $$\dfrac{1}{x}\left\lfloor\dfrac{x}{T}\right\rfloor \int_0^Tf(t)\mathrm{d}t
> \le \dfrac{1}{x}\int_0^xf(t)\mathrm{d}t
> \le \dfrac{1}{x}\left(\left\lfloor\dfrac{x}{T}\right\rfloor+1\right)\int_0^Tf(t)\mathrm{d}t.$$
>
> 或者写假设$nT \le  x < (n+1)T$, 则
> 
> $$\dfrac{1}{(n+1)T}\int_0^{nT}f(t)\mathrm{d}t \le \dfrac{1}{x}\int_0^xf(t)\mathrm{d}t
> \le \dfrac{1}{nT}\int_0^{(n+1)T}f(t)\mathrm{d}t.$$

错误原因：$f$不一定恒为非负. 

{: .problem}
> **问题3：** 由于$\displaystyle\dfrac{1}{nT}\int_0^{nT}f(t)\mathrm{d}t=\dfrac{1}{T}\int_0^Tf(t)\mathrm{d}t$, 
> 所以
>
> $$\lim\limits_{x\to+\infty}\dfrac{1}{x}\int_0^xf(t)\mathrm{d}t=
\lim\limits_{x\to+\infty}\dfrac{1}{nT}\int_0^{nT}f(t)\mathrm{d}t=\dfrac{1}{T}\int_0^Tf(t)\mathrm{d}t.$$

错误原因：未考虑$x=nT+\alpha(0 < \alpha < T)$的情况.

{: .new}
> **本题一个有意思的证明方法.**
>
> 考虑函数
>
> $$F(x)=\int_0^xf(t)\mathrm{d}t-\dfrac{x}{T}\int_0^Tf(t)\mathrm{d}t,$$ 
>
> 则$F(T)=0$, 
> 并且可以证明$F(T+x_0)=F(x_0)$, 所以$F$是连续的周期为$T$的函数, 从而必有界, 即$\vert F\vert\le M$. 则
> 
> $$\left|\dfrac{1}{x}\int_0^xf(t)\mathrm{d}t-\dfrac{1}{T}\int_0^Tf(t)\mathrm{d}t\right| = \dfrac{|F(x)|}{|x|}
\le \dfrac{M}{|x|} \to 0(x\to+\infty).$$

## 第四题

请看[第6次作业](/docs/TA/MathAnalysisA/MA_ASS6/)的助教思考题. 
本题的一个正确做法是把区间$[a,b]$取$k$等份, 得到一个不等式, 然后让$k$趋于无穷.
另外也可以验证导数的定义, 来证$f$可导并且导数恒为$0$.

{: .problem}
> **问题1：** $f$可导的问题. 直接写
> 
> $$|f'(x)|=\left|\lim\limits_{h\to 0}\dfrac{f(x+h)-f(x)}{h}\right| \le h^{\delta} \to 0(\delta\to 0).$$
>
> 或者用Lagrange中值定理.  

错误原因：写第一个等号的前提是$f$可导, 题目没说$f$可导. 本题正确做法是先说明

$$\lim\limits_{h\to 0}\dfrac{f(x+h)-f(x)}{h}=0$$

恒成立, 然后再根据导数的定义得到$f$可导且导数恒为$0$. 

{: .problem}
> **问题2：** 很容易得到$f$一致连续. 然后写: 由Lagrange中值定理, 存在$\xi$介于$x,y$之间,
> 使得$f'(\xi)=\dfrac{f(x)-f(y)}{x-y}$.

错误原因：这是第9次作业已经说了的问题. 现在不知道$f$是否可导, 就不能写“$f'$”.

{: .problem}
> **问题3：** 反证法, 若$f$不是常值函数, 取$x_0\in[a,b]$, $x_0+\varepsilon\in[a,b]$ $(\varepsilon\to 0)$,
> 故$\vert f(x_0+\varepsilon)-f(x_0)\vert > 0$, 且$\vert f(x_0+\varepsilon) - f(x_0)\vert \le L\varepsilon^{1+\delta}.$
> 当$\varepsilon\to 0$时, $L\varepsilon^{1+\delta}\to 0$, 故可得$\vert f(x_0+\varepsilon)-f(x_0)\vert \le 0$, 矛盾,
> 则$f$是常值函数.

错误原因：(1)不规范的写法, 记号$x_0+\varepsilon\in [a,b]$ $(\varepsilon\to 0)$是什么意思?

(2)$f$连续, 当然有$\lim\limits_{\varepsilon\to 0}f(x_0+\varepsilon)=f(x_0)$, 并不能推出矛盾. 

根据极限保序性, 在$\vert f(x_0+\varepsilon)-f(x_0)\vert > 0$中让$\varepsilon\to0$会得到

$$\vert f(x_0+\varepsilon)-f(x_0)\vert \ge 0.$$


## 第六题

第一个问题其实是大部分同学都犯了的错误, 但助教GG没在作业上指出来. 

{: .problem}
> **问题1：**  绝大多数同学找到$x_n$满足$f'(x_n) = -1 < 0$之后, 就直接说$f$不是单调递增. 

错误原因：利用$f'$的连续性说明在这个点的一个邻域内导数恒为负, 从而根据引理4.2.1可知$f$在这个邻域内单调递减.
仅仅一点处导数为负并不足够说明$f$不是单调递增. 

{: .problem}
> **问题2：** 说存在$\delta>0$使得$f$在$(-\delta,\delta)$单调递增, 说明方法是先证明$f'(0)=1>0$, 
> 然后说$f(x)$在$0$处连续, 从而$f(x)$连续可微, 从而存在$\delta>0$使得$f'$在$(-\delta,\delta)$都为正, 
> 从而$f$在$(-\delta,\delta)$单调递增.

错误原因：连续可微$\ne$连续且可微！

事实上, 连续可微表示可微并且**导函数连续**.


{: .problem}
> **问题3：** 证明$f'$在$0$处间断(但没有取特定的使得导数为负的点), 从而说明$f$不是单调递增.

错误原因：需要取特定的点满足$f'$为负.


## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）
