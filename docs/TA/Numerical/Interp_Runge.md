---
layout: default
title: 插值：Runge现象的本质
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 51
---

{: .note}
> 改编自我的知乎回答[https://www.zhihu.com/question/562144801/answer/2739009984](https://www.zhihu.com/question/562144801/answer/2739009984).

# 插值多项式的节点越多，误差越小吗？

不对，在$[a,b]$上对函数$f(x)$用$n$次多项式$p(x)$插值的误差公式（插值结点为$x_0,\cdots,x_n$）是

$$f(x)-p(x)=\dfrac{1}{(n+1)!}f^{(n+1)}(\xi_x)w_{n+1}(x),$$

其中$\xi_x$是位于$[a,b]$的数，并且$w_{n+1}(x)=\prod\limits_{i=0}^n(x-x_i)$. 于是

$$\|f(x)-p(x)\|_{\infty}
\le \dfrac{1}{(n+1)!}\|w_{n+1}\|_{\infty}\|f^{(n+1)}\|_{\infty}.$$

如果$\Vert f^{(n+1)}\Vert_{\infty}$关于$n$的增长速率大于$\dfrac{1}{(n+1)!}\Vert w_{n+1}\Vert_{\infty}$的衰减速率,
那么上式右边就无法控制误差，此时Newton-Cotes公式的误差会随着节点增多而增多. 

对于定义域是$[-1,1]$并且取Chebyshev多项式的根作为结点的情况, 我们有误差公式

$$|f(x)-p(x)|\le \dfrac{1}{2^n(n+1)!}\|f^{(n+1)}\|_{\infty}, $$

在书上常见的例子就是考虑对函数$f(x)=\dfrac{1}{1+4x^2}$在区间$[−5,5]$
用等距结点的多项式插值以及Chebyshev结点进行多项式插值,
可以发现前者会有“Runge现象”, 而后者没有.
这是因为用等距结点的情形下误差没法控制住, 而用Chebyshev结点的误差多了一项$\dfrac{1}{2^n}$, 此时可以把误差控制住. 

但是，在论文[Epperson, On the Runge Example](/res/Epperson.pdf)中, 证明了只要用Chebyshev结点, 就一定不会出现Runge现象,
即$p_n\to f$关于$n$在闭区间中一致收敛.