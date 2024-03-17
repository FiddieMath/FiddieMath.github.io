---
layout: default
title: 第10次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 17
---

## 第10次作业

习题4.3/6奇数题, 7, 9奇数题, 10奇数题, 11奇数题, 12奇数题.

## 主要问题

### 4.3/10(5)题

**问题：** 广义积分还没学呢, 有些同学就作换元$x=\tan t$变成广义积分. 

虽然某些“参考答案”可能是用广义积分来处理的, 
但是还没学过就不要使用, 还是得用万能变换$x=\tan \dfrac{t}{2}$.

## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

{: .note}
> 书中第6题是用递推来计算与$m,n$有关的数列, 现在我们来看一下计算与积分有关的数列极限的问题.
>
> 注意, 不一定要把积分的精确值算出来. 

**1.** 设$a>1$, 计算极限

$$\lim\limits_{n\to\infty}\int_{2n\pi}^{(2n+1)\pi}(x^a-\lfloor x^a\rfloor)\sin x\mathrm{d}x,$$

其中, $\lfloor x\rfloor$表示不超过$x$的最大整数.

**2.** 计算极限:

(1)$\displaystyle\lim\limits_{n\to\infty}\int_0^1\dfrac{x^n}{1+x}\mathrm{d}x$.

(2)$\displaystyle\lim\limits_{n\to\infty}\int_0^1nx(1-x^2)^n\mathrm{d}x$.

(3)$\displaystyle\lim\limits_{n\to\infty}\int_1^2\dfrac{\sin(nx)}{x}\mathrm{d}x$.

{: .remark}
> 一般情况下积分和极限不可交换, 即
> $\lim\limits_{n\to\infty} \int_a^b f_n(x)\mathrm{d}x \ne \int_a^b  \lim\limits_{n\to\infty}f_n(x)\mathrm{d}x $.

**3.** 
(1)**(习题6.2/9的弱化版本)** 设$f$是$\mathbb{R}$上周期为$T$的连续函数, $g$是$[a,b]$上的连续函数, 则

$$\lim\limits_{n\to\infty}\int_a^bf(x)g(nx)\mathrm{d}x=\dfrac{1}{T}\int_0^Tf(x)\mathrm{d}x\cdot\int_a^bg(x)\mathrm{d}x.$$

(2)用(1)的结论或者其他方法来计算极限:

$$\lim\limits_{n\to\infty}\int_0^{\pi}\dfrac{\sin x}{1+\cos^2nx}\mathrm{d}x.$$


&nbsp; 

&nbsp;

{: .note}
> 下面的Nagumo定理在变分法和最优控制中会用到. 
>

**4.(Nagumo定理)** 若$f$是$[0,1]$上的非负连续函数, $f(0)=0$, $\lim\limits_{t\to 0}\dfrac{f(t)}{t}=0$, 
并且满足对任意$t\in[0,1]$, 

$$f(t)\le \int_0^t\dfrac{f(s)}{s}\mathrm{d}s,$$

则$f$恒为$0$. 

{: .remark}
> 考虑常微分方程
>
> $$x'(t)=f(t,x(t)),$$
>
> 初始条件为$x(0)=0$, $a>0$, $f:[0,a]\times\mathbb{R}\to\mathbb{R}$是连续函数, $f(t,0)=0$, $t\in[0,a]$. 
> 则当
> 
> $$|f(t,x)-f(t,y)|\le\dfrac{|x-y|}{t}, \forall t\in(0,a], x,y\in\mathbb{R}, \text{且}\exists M>0, |x|, |y|\le M$$
>
> 时, 根据Nagumo定理可知这个常微分方程的解是唯一的. 

&nbsp; 

&nbsp;

{: .note}
> 下面的Gronwall定理在常微分方程(大二上学期课程)中会用到, 用来证明微分方程存在唯一解. 
>

**5.(Gronwall不等式)** 设有四个定义在$\mathbb{R}^+$的非负连续函数$a,b,c,f$, 满足对任意$x\ge 0$, 有

$$f(x)\le \int_0^x[a(t)f(t)+b(t)]\mathrm{d}t + c(x),$$

证明Gronwall不等式

$$f(x)\le \left[\int_0^xb(t)\mathrm{d}t+\max\limits_{t\in[0,x]}c(t)\right]e^{\int_0^xa(t)\mathrm{d}t}.$$

**6.** 假设存在定义在$[0,+\infty)$上的$C^1$函数$x(t)$满足

$$\left\{\begin{aligned}
&x'(t)=x(t)t+\sin(t^2+x(t)) \\
&x(0)=x_0 \\
\end{aligned}\right. \qquad (*)$$

证明满足$(*)$式的$x(t)$是唯一的. 



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

**1.** 答案为$1$. 

**2.** (1)【方法一】可以直接计算出$\displaystyle\int_0^1\dfrac{x^n}{1+x}\mathrm{d}x$的结果, 

【方法二】固定$\delta\in(0,1)$, 然后拆分

$$\int_0^1\dfrac{x^n}{1+x}\mathrm{d}x=\int_0^{\delta}\dfrac{x^n}{1+x}\mathrm{d}x
+\int_{\delta}^1\dfrac{x^n}{1+x}\mathrm{d}x\triangleq I_1+I_2.$$

然后分别证明$0 < I_1 < \dfrac{\varepsilon}{2}, 0 < I_2 < \dfrac{\varepsilon}{2}.$

(2)直接计算积分为$\dfrac{n}{2(n+1)}$.

(3)用一次分部积分, 然后再作放缩. 

**3.** 把这个积分和下面的式子作比较: 

$$\sum\limits_{k=1}^n\int_{\frac{k-1}{n}(b-a)}^{\frac{k}{n}(b-a)}f\Big(\frac{k}{n}(b-a)\Big)g(x)\mathrm{d}x.$$

**4.** 若$f(t_0)>0$, 研究$\sup\limits_{t\in [0,t_0]}\dfrac{f(t)}{t}$. 

**5.** 建立函数$\displaystyle F(x)=\int_0^x[a(t)f(t)]\mathrm{d}t$的不等式,
再考虑函数$A(x)=F(x)e^{-\int_0^xa(t)\mathrm{d}t}$. 

**6.** 用Gronwall不等式.

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

## 部分题的解答

**4.** (反证法)若存在$x_0\in(0,1]$使得$f(t_0)>0$, 则$\dfrac{f(t_0)}{t_0}>0$. 
根据连续函数最值定理以及$\lim\limits_{t\to 0}\dfrac{f(t)}{t}=0$, 
存在$t_1\in (0,t_0]$使得

$$M=\sup\limits_{t\in[0,t_0]}\dfrac{f(t)}{t} = \dfrac{f(t_1)}{t_1}.$$

再由于$\lim\limits_{t\to 0}\dfrac{f(t)}{t}=0$, 所以存在$\delta>0$, 使得当$0 < t < \delta$时, 
有$\dfrac{f(t)}{t} < \dfrac{M}{2}$. 

因此, 

$$\begin{aligned}
t_1M = f(t_1) &\le \int_0^{t_1}\dfrac{f(s)}{s}\mathrm{d}s \\
&=\int_0^{\delta}\dfrac{f(s)}{s}\mathrm{d}s + \int_{\delta}^{t_1}\dfrac{f(s)}{s}\mathrm{d}s \\
&\le \dfrac{M}{2}\delta + M(t_1-\delta) \\
& < t_1M.
\end{aligned}$$

产生矛盾. 因此$f$必定恒为$0$. 

**5.** 令$\displaystyle F(x)=\int_0^xa(t)f(t)\mathrm{d}t$, 由于$a,f$都是连续函数, 则$F\in C^1$, 从而

$$F'(x)=a(x)f(x) \le a(x)F(x)+a(x)\left(\int_0^xb(t)\mathrm{d}t+\max\limits_{t\in[0,x]}c(t)\right).$$

再定义$\displaystyle A(x)=F(x)e^{-\int_0^xa(t)\mathrm{d}t}$, 于是

$$A'(x)=[F'(x) - a(x)F(x)]e^{-\int_0^xa(t)\mathrm{d}t}\le a(x)\left(\int_0^xb(t)\mathrm{d}t+\max\limits_{t\in[0,x]}c(t)\right)e^{-\int_0^xa(t)\mathrm{d}t},$$

因此, 

$$\begin{aligned}
F(x)&= e^{\int_0^xa(t)\mathrm{d}t}A(x) \\
&=e^{\int_0^xa(t)\mathrm{d}t}\int_0^xA'(t)\mathrm{d}t \\
&\le e^{\int_0^xa(t)\mathrm{d}t}\int_0^x \left(a(t)\left(\int_0^tb(s)\mathrm{d}s+\max\limits_{s\in[0,t]}c(s)\right)e^{-\int_0^ta(s)\mathrm{d}s}\right)\mathrm{d}t \\
&\le e^{\int_0^xa(t)\mathrm{d}t}\left(\int_0^xb(s)\mathrm{d}s+\max\limits_{s\in[0,x]}c(s)\right)\int_0^x  a(t)e^{-\int_0^ta(s)\mathrm{d}s} \mathrm{d}t\\
&=e^{\int_0^xa(t)\mathrm{d}t}\left(\int_0^xb(s)\mathrm{d}s+\max\limits_{s\in[0,x]}c(s)\right)\int_0^x  \dfrac{\mathrm{d}}{\mathrm{d}t}\left(-e^{-\int_0^ta(s)\mathrm{d}s}\right) \mathrm{d}t\\
&=e^{\int_0^xa(t)\mathrm{d}t}\left(\int_0^xb(s)\mathrm{d}s+\max\limits_{s\in[0,x]}c(s)\right)\left[1-e^{-\int_0^xa(s)\mathrm{d}s}\right]
\end{aligned}$$

因此回到一开始的不等式可知

$$\begin{aligned}
f(x)&=F(x)+\int_0^xb(s)\mathrm{d}s+c(x) \\
&\le \left(\int_0^xb(s)\mathrm{d}s+\max\limits_{s\in[0,x]}c(s)\right)\left[e^{\int_0^xa(s)\mathrm{d}s}-1\right]
+\int_0^xb(s)\mathrm{d}s+c(x) \\
&\le \left(\int_0^xb(s)\mathrm{d}s+\max\limits_{s\in[0,x]}c(s)\right)e^{\int_0^xa(s)\mathrm{d}s}.
\end{aligned}$$

**6.** 假设$\psi(t), \phi(t)$同时满足

$$\left\{\begin{aligned}
&\psi'(t)=\psi(t)t+\sin(t^2+\psi(t)) \\
&\varphi'(t)=\varphi(t)t+\sin(t^2+\varphi(t)) \\
\end{aligned}\right.$$

由Newton-Leibniz公式, 

$$\left\{\begin{aligned}
&\psi(t)-x_0=\int_0^t \psi(s)s+\sin(s^2+\psi(s))\mathrm{d}s \\
&\varphi(t)-x_0=\int_0^t \varphi(s)s+\sin(s^2+\varphi(s))
\end{aligned}\right.$$

两式作差, 可得

$$\begin{aligned}
|\psi(t)-\varphi(t)|&=\left|\int_0^t(\psi(s)-\varphi(s))s+\sin(s^2+\psi(s))-\sin(s^2+\varphi(s))\mathrm{d}s\right| \\
&\le \int_0^t\left( |\psi(s)-\varphi(s)|s + 2\left|\cos\dfrac{2s^2+\psi(s)+\varphi(s)}{2}\sin\dfrac{\psi(s)-\varphi(s)}{2}\right| \right) \mathrm{d}s \\
&\le \int_0^t \left(|\psi(s)-\varphi(s)|s + 2\cdot\dfrac{1}{2}|\psi(s)-\varphi(s)|\right)\mathrm{d}s \\
&= \int_0^t|\psi(s)-\varphi(s)|(s+1)\mathrm{d}s.
\end{aligned}$$

根据Gronwall不等式(在Gronwall不等式中让$f(t)=\vert\psi(t)-\varphi(t)\vert$, $a(t)=t+1$, $b(t)=c(t)=0$, 可知

$$|\psi(t)-\varphi(t)|\le 0.$$

即$\psi(t)=\varphi(t)$. 因此满足$(*)$的函数$x(t)$是唯一的. 




