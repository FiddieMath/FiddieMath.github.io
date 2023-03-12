---
layout: default
title: 补充内容：Fejér-Jackson不等式
parent: 数学分析A
grand_parent: 助教工作
nav_order: 23
---

我在B站发布了视频讲解：[https://www.bilibili.com/video/BV1wb41197fS](https://www.bilibili.com/video/BV1wb41197fS). 

下面这个问题是Fejér在1910年提出, 然后被Jackson证明的. 后面有许多人尝试改进它的上、下界, 但技巧性太强, 这里不做介绍.

{: .problem}
> 证明：当$x\in(0,\pi)$时, $\sum\limits_{k=1}^{2023}\dfrac{1}{k}\sin kx>0$. 

**证明：** 我们证明一般的情形. 

记$f_n(x)=\sum\limits_{k=1}^n\dfrac{\sin kx}{k},$ 则

$$\begin{aligned}
f_n'(x)&=\sum\limits_{k=1}^n\cos kx \\
&=\mathrm{Re}\sum\limits_{k=1}^n(e^{ix})^k \\
&=\mathrm{Re}\left(e^{ix}\dfrac{e^{inx}-1}{e^{ix}-1}\right) \\
&=\dfrac{\cos\frac{(n+1)x}{2}\sin\frac{nx}{2}}{\sin\frac{x}{2}}.
\end{aligned}$$

于是, $f_n'(x)$的所有零点$x$满足

$$\dfrac{nx}{2}=k\pi(k\in\mathbb{Z}), \qquad\text{与}\dfrac{(n+1)x}{2}=\dfrac{\pi}{2}+k\pi(k\in\mathbb{Z}).$$

在$(0,\pi)$上, 这些零点从小到大排列为

$$0 < \dfrac{\pi}{n+1} < \dfrac{2\pi}{n} < \dfrac{3\pi}{n+1} < \dfrac{4\pi}{n} < \cdots < \dfrac{2\lfloor n/2\rfloor\pi}{n}\le \pi.$$

在$(0,\dfrac{\pi}{n+1})$上, $f_n'(x)>0$. 于是, 从$0$开始往$x$轴正方向, 每经过一个零点, $f_n'(x)$的符号就变化一次. 
从而

$$\dfrac{2\pi}{n}, \dfrac{4\pi}{n},\cdots,\dfrac{2\lfloor n/2\rfloor\pi}{n}$$

是$f_n(x)$的所有极小值点. 

下面用数学归纳法来证明$f_n(x)>0$在$(0,\pi)$上成立. 

(i)首先当$n=1$时$f_1(x)=\sin x$, 结论显然成立. 

(ii)下面假设$f_{n-1}(x)>0$在$(0,\pi)$上成立(其中$n\ge 2$).

注意到, 对$j=1,2,\cdots,\lfloor n/2\rfloor$, 

$$f_n\left(\dfrac{2j\pi}{n}\right)
=f_{n-1}\left(\dfrac{2j\pi}{n}\right) + \sin \left(n\cdot\dfrac{2j\pi}{n}\right) = f_{n-1}\left(\dfrac{2j\pi}{n}\right) >0,$$

最后的不等号是因为归纳假设. 于是, $f_n(x)$在所有极小值点处都大于$0$, 从而$f_n(x)>0$在$(0,\pi)$上恒成立. $\square$


