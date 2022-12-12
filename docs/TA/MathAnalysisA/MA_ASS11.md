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

错误原因：我们还没学过积分和极限在什么情况下可交换, 所以类似于

$$\lim\limits_{n\to\infty}\int_{a_n}^{b_n}f_n(x)\mathrm{d}x
= \int_a^b\lim\limits_{n\to\infty}f_n(x)\mathrm{d}x$$

的步骤都算是错的.  (这里$a_n\to a$, $b_n\to b$)

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

$$u_n\int_{a_n}^{b_n}g(x)\mathrm{d}x \le \int_a^bf_n(x)\mathrm{d}x\le v_n\int_{a_n}^{b_n}h(x)\mathrm{d}x,$$

然后不等号两边看成数列, 对两边求$n\to\infty$数列极限, 
从而得到$\lim\limits_{n\to\infty}\int_a^bf_n(x)\mathrm{d}x$的值.

{: .new-title}
> 正确的例子
>
> $\displaystyle\lim\limits_{n\to\infty}\int_1^{(1+\frac{1}{n})^n}\dfrac{\sqrt{1+t}}{t}\mathrm{d}t
=\int_1^e\dfrac{\sqrt{1+t}\mathrm{d}t}{t}.$

这就是把$\displaystyle \int_1^{(1+\frac{1}{n})^n}\dfrac{\sqrt{1+t}}{t}\mathrm{d}t$看成数列,
那么这个数列的极限就是$\displaystyle\int_1^e\dfrac{\sqrt{1+t}\mathrm{d}t}{t}$,
可以利用学过的知识进行解释.

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

错误原因：单调有界原理只是用来证明极限存在, 并不能用来算极限.

{: .problem}
> **问题4：** 消失的$\lim$. 

错误原因：写着写着就把$\lim$丢掉了. 

{: .warning-title}
> 错误的例子
>
> $\displaystyle \lim\limits_{m\to\infty}\sum_{i=1}^m\sqrt{1+\left[\left(1+\dfrac{i}{m}\dfrac{1}{n}\right)^{n\cdot\frac{m}{i}}\right]^{\frac{i}{m}}}(x_i-x_{i-1})
= \lim\limits_{m\to\infty} \sum_{i=1}^m\sqrt{1+e^{\frac{i}{m}}}(x_i-x_{i-1}).$

错误原因：这个例子中就算加了$n\to\infty$也还是错, 需要保证$m\to\infty$和$n\to\infty$两个极限过程可交换,
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

错误原因：首先, 题目没说$f$可导，出现$f'$都算错. 

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

{: .problem}
> **问题4：** 分类讨论$f(x)$是否连续. 若$f(x)$连续, 则$\lim\limits_{x\to x_0}\dfrac{f(x)-f(x_0)}{x-x_0}=f'(x_0)$. 

首先没必要分类讨论, $f(x)$连续可直接证出来.
其次, $f(x)$连续推不出$\lim\limits_{x\to x_0}\dfrac{f(x)-f(x_0)}{x-x_0}=f'(x_0)$. 


## 第六题

第一个问题其实是大部分同学都犯了的错误, 但助教哥哥没在作业上指出来. 

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

## 第七题

{: .problem}
> **问题1：** 由Roller定理(不止一位同学)

把“Rolle”拼成“Roller”了, Rolle哭晕在厕所.


{: .problem}
> **问题2：** 考虑$F_n(x)=\dfrac{\mathrm{d}^n}{\mathrm{d}x^n}(e^{-\frac{x^2}{2}})$, 
> 
> 用归纳法, 假设$F_k(x)=f_k(x)e^{-\frac{x^2}{2}}$有$k$个零点$x_1 < x_2 < \cdots < x_k$, 
> 且$\lim\limits_{x\to+\infty}F_k(x)=0$, $\lim\limits_{x\to-\infty}F_k(x)=0$, 
>
> 由于$f_{k+1}(x)=f_k'(x)-xf_k(x)$, 所以存在$y_1,y_2,\cdots,y_{k+1}$, 使得
> 
> $$y_1 < x_1 < y_2 < x_2 < \cdots < y_k < x_k < y_{k+1}, F_{k+1}(y_i)=0, i=1,2,\cdots,k+1.$$

错误原因：跳步了, 建议改为用归纳法证明$f_k'(x_j)(j=1,2,\cdots,k)$的相邻两个的符号相反.

当然, 更快的方法是直接考虑$F_n(x)$的零点, 用Rolle定理.

{: .problem}
> **问题3：** $F_n(x)=f_n(x)e^{-\frac{x^2}{2}}$. 由于$f_n(x)$为$n$次多项式, 根据代数基本定理,
> 复数域上$n$次多项式有$n$个根, 所以$f_n(x)$有$n$个零点, 所以$F_n(x)$有$n$个零点.

错误原因：题目要求证明有$n$个“不同”零点, 这里没考虑重根的情形. 
另外, 可以证明$F_n(x)$的根都是实根.

## 第八题

{: .problem}
> **问题1：** 出现$f'(x)$.

错误原因：题目没说$f$可导.

{: .problem}
> **问题2：** Lipschitz系数与$x,y$有关.

错误原因：需要利用$f(x)$的有界性把Lipschitz系数放缩为常数.

## 第九题

下面几个问题基本上都算是混淆了“导函数存在”和“导函数连续”的概念.

{: .problem}
> **问题1：** 由于$f$可导, 所以$\lim\limits_{x\to x_0^+}\dfrac{f(x)-f(x_0)}{x-x_0}=\lim\limits_{x\to x_0^+}f'(x)=f'(x_0)$. 

错误原因：$f$可导的定义是下面极限存在

$$\lim\limits_{x\to x_0}\dfrac{f(x)-f(x_0)}{x-x_0}$$

把这个极限的值记为$f'(x_0)$. 而并不是

$$\lim\limits_{x\to x_0^+}\dfrac{f(x)-f(x_0)}{x-x_0}=\lim\limits_{x\to x_0^+}f'(x), \tag{9.1}$$

一般情况下这是错的. 反例: 第六题, $f$在$0$处可导, 但$\lim\limits_{x\to 0^+}f'(x)$并不存在. 

只有当$f'(x)$右连续时, $(9.1)$式才是对的.

{: .problem}
> **问题2：** 反证法, 若$f'(x)$在$(a,b)$上有间断点$x_0$, 由$f'(x)$在$(a,b)$上单调, 则$x_0$必为跳跃间断点, 
> 即$\lim\limits_{x\to x_0^-}f'(x)\ne\lim\limits_{x\to x_0^+}f'(x)$. 这与$f(x)$在$(a,b)$上可导矛盾.

错误原因: $\lim\limits_{x\to x_0^-}f'(x)\ne\lim\limits_{x\to x_0^+}f'(x)$只能推出$f'$在$x_0$处不连续.

既然能写出$f'(x)$这样的记号, 前提条件必须是$f(x)$可导. 

{: .problem}
> **问题3：** 由$f$可导, 则$f_+'(x_0)=f_-'(x_0)=f'(x_0)$, 所以$\lim\limits_{x\to x_0^+}f'(x)=\lim\limits_{x\to x_0^-}f'(x)=f'(x_0)$. 

错误原因: 前半句是正确的, 导数相同当且仅当左导数和右导数相同. 但是后半句是错误的, 一般情况下
$f_+'(x_0)= \lim\limits_{x\to x_0^+}f'(x)$
并不成立, 这个式子表示$f'(x)$右连续. 

同问题1, 反例是第六题, $f$在$0$处可导, 但$\lim\limits_{x\to 0^+}f'(x)$并不存在. 

{: .problem}
> **问题4：** 由于$f_+'(x_0)=\lim\limits_{x\to x_0^+}\dfrac{f(x)-f(x_0)}{x-x_0}$, 
> 根据Lagrange中值定理, 存在$\xi_x\in(x_0,x)$, 使得$f'(\xi_x)=\dfrac{f(x)-f(x_0)}{x-x_0}$,
> 所以
>
> $$f_+'(x_0)=\lim\limits_{x\to x_0^+}f'(\xi_x)=\lim\limits_{x\to x_0^+}f'(x).$$

错误原因: 首先$\xi_x\to x_0(x\to x_0)$是对的, 但是, 只有当$f'$右连续才能写

$$\lim\limits_{x\to x_0^+}f'(\xi_x)=\lim\limits_{x\to x_0^+}f'(x).$$

但$f'$连续是题目要你证的, 这里属于典型的用结论证结论的情况了.

## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**0.** 举例题. 

(1)举例说明$f\in\mathrm{Lip}$不一定能推出$f$可导.

(2)举例说明存在$f$, 满足$f\notin\mathrm{Lip}[0,1]$但对任意$\delta>0$, $f\in\mathrm{Lip}[\delta,1]$. 

&nbsp; 

&nbsp; 

**1.** 设

$$f(x)=\left\{\begin{aligned}
&x^2\sin\dfrac{1}{x}, &&x\ne 0, \\
&0, &&x=0, 
\end{aligned}\right.$$

在$[0,x]$上应用Lagrange中值定理, 得

$$x^2\sin\dfrac{1}{x}=x\left(2\xi\sin\dfrac{1}{\xi}-\cos\dfrac{1}{\xi}\right) ( 0 < \xi < x).$$

即得

$$\cos\dfrac{1}{\xi}=2\xi\sin\dfrac{1}{\xi}-x\sin\dfrac{1}{x}.$$

当$x\to 0$时, 有$\xi\to 0$, 所以由上式得到

$$\lim\limits_{\xi\to 0}\cos\dfrac{1}{\xi}=0.$$

但已知$\lim\limits_{\xi \to 0}\cos\dfrac{1}{\xi}$不存在. 请说明上面的步骤中哪里出现了问题?


&nbsp; 

&nbsp; 

**2.** 设$p:\mathbb{R}\to\mathbb{R}$是一个$n$次多项式, 并且处处非负. 证明: 对任意$x\in\mathbb{R}$, 都有

$$p(x)+p'(x)+p''(x)+\cdots+p^{(n)}(x)\ge 0.$$

&nbsp; 

&nbsp; 

**3.** 设连续函数$g:[0,+\infty)\to\mathbb{R}^+$, 定义函数$\displaystyle f(t)=g(t)\int_0^t[g(s)]^{-a}\mathrm{d}s$, 

(1)若$a>1$, 证明：$f(t)$是无界函数. 

(2)当$a=1$时, (1)中的结论还对吗?  

&nbsp; 

&nbsp; 

**4.(Wronski行列式)** 设$f,g$是可微函数, 行列式

$$W_{f,g}(x)=\begin{vmatrix} f(x) & g(x) \\ f'(x) & g'(x)\end{vmatrix}$$

称为**Wronski行列式**, 在大二的《常微分方程》课中会用到. 若$W_{f,g}$在区间$I$上没有零点, 
并且对于$x_1,x_2\in I(x_1 < x_2)$有$f(x_1)=f(x_2)=0$, 
证明: 存在$x_3\in(x_1,x_2)$使得$g(x_3)=0$. 

(例如: $f(x)=\sin x, g(x)=\cos x$是满足条件和结论的一个例子)


&nbsp;

&nbsp; 

**5.(*)** 假设多项式$P_n$满足$P_0=1$, $P_1=x+1$, $P_{n+1}=P_n+xP_{n-1}$, 
证明: 对任意正整数$m$, 多项式$P_m$的所有根都为实数.

&nbsp; 

&nbsp; 

**6.** 设$f$是定义在区间$I$上的函数, 给定下面两个命题：

(1)下面不等式成立: (注：$\det A$表示$A$的行列式, $\vert \det A\vert$表示$A$的行列式的绝对值. )

$$\left\vert \det\begin{pmatrix} f(u) & f(v) & f(w) \\ u&v&w \\ 1&1&1\end{pmatrix} \right\vert
\le \vert(u-v)(v-w)(w-u)\vert;$$

(2)$f$可微, 且$f'$是Lipschitz连续函数, 并且Lipschitz常数是2. 
(即$\vert f'(x)-f'(y)\vert \le 2\vert x-y\vert$, $\forall x,y\in I.$)

证明: $(1)\Leftrightarrow(2)$.

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

&nbsp; 

&nbsp;

## 提示

{: .remark}
> 本次的第2、4、5、6题的目的是为了让同学们意识到, 数学分析和高等代数并不是割裂的, 两者之间可以相互结合.
> 第5题长得很像作业第七题, 然而如果用数学分析的方法(Rolle定理)是没办法做出来的. 这时就需要从纯代数的角度去思考这个问题了.

**0.** (1)$f(x)=\vert x\vert$. (2)$f(x)=\sqrt{x}$.

**1.** 当$x\to 0$时, 有$\xi\to 0$并没错, 但是$\xi$是跟$x$有关的, 我们把$\xi$改写为$\xi(x)$, 即看成$x$的函数,
那么只能得到

$$\lim\limits_{x\to 0}\cos\dfrac{1}{\xi(x)}=0.$$

**2.** 考虑函数$H(x)=p(x)+p'(x)+p''(x)+\cdots+p^{(n)}(x)$, 比较$H,H',p$的关系.

**3.** (2)考虑$g(t)=e^{-t}$, 则$f(t)=1-e^{-t}$是有界函数.

**4.** 若$g$在$(x_1,x_2)$上没有零点, 对函数$\dfrac{f(x)}{g(x)}$应用Rolle定理. 


**5.** 反证法, 若存在$P_n$有复根, 设$m$是使得$P_{m+1}$具有复根的最小的正整数, 
证明如果$P_{m+1}$具有复根, 则$P_{m-1}$有复根, 这与$m$的选取矛盾.

具体来说, 考虑$x=u+iv$, 定义数列$r_n$和$s_n$分别为$P_n(x)$的实部和虚部, 则

$$r_{n+1}+is_{n+1}=r_n+is_n+(u+iv)(r_{n-1}+is_{n-1}),$$

从而$r_{n+1}=r_n+ur_{n-1}-vs_{n-1}$且$s_{n+1}=s_n+vr_{n-1}+us_{n-1}$.

若存在一个$P_n$具有复根, 我们假设$m$是最小的正整数使得$P_{m+1}$的复根为$a+bi$,
由于$P_{m+1}$是实系数多项式, 则$a-bi$也是复根. 因此

$$\begin{aligned}
r_{m+1}=0=r_m+ar_{m-1}-bs_{m-1}=r_m+ar_{m-1}+bs_{m-1}, \\
s_{m+1}=0=s_m+br_{m-1}+as_{m-1}=s_m-br_{m-1}+as_{m-1}.
\end{aligned}$$

因此, $-bs_{m-1}=bs_{m-1}$且$br_{m-1}=-br_{m-1}$. 由于$b\ne 0$, 则$s_{m-1}=0=r_{m-1}$.
这样, $a+bi$是$P_{m-1}$的复根, 这与$m$的选取矛盾. 


**6.** “$\Leftarrow$”: 用Newton-Leibniz公式来处理, 行列式可以变成下式: 

$$\begin{aligned}
|\det(\cdot)|&=\left|\int_v^uf'(t)\mathrm{d}t (v-w)+\int_v^wf'(s)(u-v)\mathrm{d}s\right| \\
&=\left|\int_w^v\int_v^uf'(t)\mathrm{d}t\mathrm{d}s-\int_w^v\int_v^uf'(s)\mathrm{d}t\mathrm{d}s\right| \\
&=\left|\int_w^v\int_v^u[f'(t)-f'(s)]\mathrm{d}t\mathrm{d}s\right|.
\end{aligned}$$

接下来就用Lipschitz条件进行放缩即可.

“$\Rightarrow$”: 把行列式改写成下面的形式: 

$$\left|\dfrac{f(u)-f(v)}{u-v}-\dfrac{f(w)-f(v)}{w-v}\right|\le|w-u|, \tag{6.1}$$

固定$v,w$, 然后记函数$g(w)=\dfrac{f(u)-f(v)}{u-v}-\dfrac{f(w)-f(v)}{w-v} (w\ne v, w\in I)$, 
则$g$是Lipschitz函数, 从而连续. 从而$\lim\limits_{w\to v}g(w)$存在, 进而推出$f$可微.

接下来对$(6.1)$式让$u\to v$, 得到关于$f'(v)$的不等式

$$\left|f'(v)-\dfrac{f(w)-f(v)}{w-v}\right|\le|w-v|, \tag{6.2}$$

把$\vert f'(x)-f'(y)\vert$用绝对值不等式写成三个绝对值, 根据$(6.1)$式和$(6.2)$式可以得到$f'$是Lipschitz连续.
