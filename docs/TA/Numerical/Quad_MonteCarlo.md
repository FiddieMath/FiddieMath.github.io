---
layout: default
title: 数值积分：Monte Carlo方法
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 101
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


# Monte Carlo方法

## 置信区间

对于独立重复试验, 假设成功的概率为$p$,
而做了$n$次独立重复试验以后观测到的成功次数为$m$,
那么我们估计成功概率是$\hat{p}=\dfrac{m}{n}$($\hat{p}$是个随机变量, 即$n\hat{p}\sim B(n,p)$,
于是$n\hat{p}$的方差是$np(1-p)$, 故$\hat{p}$的方差是$\dfrac{p(1-p)}{n}$).

我们知道, 当$n$趋于无穷时, 二项分布近似正态分布, 因此取$n$充分大之后, 可以近似看做

$$\hat{p}\sim N\left(p,\dfrac{p(1-p)}{n}\right).$$

对于一个服从正态分布的随机变量$X\sim N(\mu, \sigma^2)$,
通过正态分布表我们知道

$$P\left(-1.96 < \dfrac{X-\mu}{\sigma} < 1.96\right)=0.95.$$

因此, 代入$X=\hat{p}$, $\mu=p$, $\sigma=\sqrt{\dfrac{p(1-p)}{n}}$,
我们可以得到

$$P\left(\hat{p}-1.96\sqrt{\frac{p(1-p)}{n}} < p < \hat{p}+1.96\sqrt{\frac{p(1-p)}{n}}\right)
=0.95.$$

我们把区间$\left[\hat{p}-1.96\sqrt{\frac{p(1-p)}{n}},
\hat{p}+1.96\sqrt{\frac{p(1-p)}{n}}\right]$称为**$\mathbf{95\%}$置信区间**.

根据上面的讨论可知, $95\%$置信区间的长度是$2\times 1.96\sqrt{\dfrac{p(1-p)}{n}}.$

类似地, 我们可以知道$99\%$置信区间的长度是$2\times 2.57\sqrt{\dfrac{p(1-p)}{n}}.$

一般情况下我们不知道$p$的真实值, 所以用$\hat{p}$来代替$p$.

## 用Monte Carlo方法估计$\pi$的近似值

为了计算$\pi$的近似值, 我们可以采用Monte-Carlo方法:
随机在正方形区域$[0,1]\times[0,1]$中撒点,
计算出位于以圆心为原点、半径为1的四分之一圆的点的占比$\hat{p}$.
假如我们撒了$n$个点后, 有$m$个点位于四分之一圆中, 那么我们有$\hat{p}=\dfrac{m}{n}$.

{: .problem}
> (1)当我们撒$n$个点时, 对应的$95\%$置信区间的长度是多少?
> 
> (2)在$95\%$的置信水平的前提下, 为了保证让$\pi$至少有两位小数点的精度, 需要撒多少个点?
> 
> (3)写一个简单的程序实现用Monte-Carlo方法计算$\pi$的近似值.

## 用Monte Carlo方法计算多重积分

我们用Monte-Carlo方法来计算$d$维球$B_d$的体积, 其中

$$B_d=\{x\in\mathbb{R}^d: \|x\|_2\le 1\},$$

这里$\|x\|_2=\sqrt{x_1^2+\cdots+x_d^2}$. 计算$B_d$可以通过如下的积分来得到:

$$\mathrm{vol}(B_d)=\int_{\mathbb{R}^d}\chi(x)\mathrm{d}x_1\cdots\mathrm{d}x_d,$$

其中, 

$$\chi(x)=\left\lbrace\begin{aligned}&1, &&x\in B_d, \\ &0, &&x\notin B_d.\end{aligned}\right..$$

{: .problem}
> (1)在Python或Matlab中, 写一个函数```HyperballVolume(dim,n)```,
其中, 输入值```dim```是维数, ```n```是点的个数.
返回值为体积的估计值和$99\%$置信区间的长度.
> 
> (2)取$n=10^7$, 画出维数$1\le d\le 15$情形关于体积的折线图, 并显示$99\%$置信区间范围. 下图是取$n=10^6$情形的样例图.
> 
> {: .remark}
> > (1)请不要使用$B_d$体积的精确表达式来计算置信区间.
> > 
> > (2)如果同学们会写并行算法, 那么在随机采样的步骤可以并行化处理, 速度会更快.


<div align = center>
<img src="/pics/MC1.png" width = "400"/>

<br/>

图1：体积$B_d$关于维数$d$在$1\le d\le 15$的折线图与$99\%$置信区间
</div>
