---
layout: default
title: 补充内容：处处不可导的连续函数
parent: 数学分析A
grand_parent: 助教工作
nav_order: 14
---

# 处处不可导的连续函数

我们要举一个处处不可导的连续函数的简单例子. 
更多例子可以参考
- Johan Thim, 2003, Continuous Nowhere Differentiable Functions, Master Thesis. (点击[这里](/res/JohanThim.pdf)下载)
- Marek Jarnicki, Peter Pflug. 2015, Continuous Nowhere Differentiable Functions. 10.1007/978-3-319-12670-8.  
(点击[这里](/res/JarnickiMonster.pdf)下载)


1930年, 荷兰数学家范·德·瓦尔登(Van der Waerden, 1903-1996)构造了一个处处不可导的连续周期函数.

设

$$\Psi_0(x)=\left\{\begin{aligned}
&x, &&0\le x\le\frac{1}{2}, \\
&1-x, &&\frac{1}{2}\le x\le 1,
\end{aligned}\right.$$

并以周期1延拓这个函数到全数轴. 延拓后的周期函数用$\varphi_0$表示. 还设

$$\varphi_n(x)=\dfrac{1}{4^n}\varphi_0(4^nx).$$

那么函数$\varphi_n$的周期是$4^{-n}$, 并且除了点$x=\dfrac{k}{2^{n+1}}(k\in\mathbb{Z})$之外处处有导数,
导数等于1或$-1$. 设

$$f(x)=\sum\limits_{n=1}^{\infty}\varphi_n(x),$$

则函数$f$在$\mathbb{R}$上有定义且连续, 但处处没有导数. 



{: .remark}
> 具体可以看梅加强《数学分析》的第8章第4节(在264页). 