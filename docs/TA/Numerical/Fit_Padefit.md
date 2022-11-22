---
layout: default
title: 函数拟合：Pade逼近
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 192
---

{: .no_toc }

<details open markdown="block">
  <summary>
    目录
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

{: .new}
> 待补充完整. 

给定一些数据$\lbrace (x_i,y_i)\rbrace_{i=1}^m$, 其中$x_i\in\mathbb{R}^d$, $y_i\in\mathbb{R}$. 
我们想用函数$y=f(x)$来拟合这些数据. 
由于$(x_i,y_i)$不一定都在这条曲线上, 所以会有误差. 我们一般用**均方误差(Mean-square Loss)**, 即

$$\mathcal{L}(f)=\dfrac{1}{m}\sum\limits_{i=1}^m|f(x_i)-y_i|^2$$

来衡量误差. 我们把$\mathcal{L}$称为损失函数. 
在求$f$的表达式的时候, 通过一定的优化方法让损失函数$\mathcal{L}$尽可能小, 即求解如下的优化问题, 使得可以得到一个近似的拟合函数： 

$$\inf\limits_{f\in \mathcal{F}}\mathcal{L}(f),$$

其中$\mathcal{F}$是由一族函数构成的集合. 

在[前一节](../Fit_Polyfit/#广义多项式拟合), 我们介绍了用广义多项式

$$f(x)=\sum\limits_{k=0}^{n}a_k\phi_k(x).$$

来作拟合的方法, 其中$\phi_k(k=1,2,\cdots,n)$可以是一般的非线性函数.
但是, 在有些情况下，我们想要作拟合的函数没有办法写成上式的形式, 
例如用**有理函数(rational function)**

$$f(x)=\dfrac{P(x)}{Q(x)}$$

来作逼近, 其中$P(x),Q(x)$都是多项式, 其系数都是未知的. 用有理函数作逼近的方法叫做**Pade(帕德)逼近**.

## Pade逼近

### 算例：