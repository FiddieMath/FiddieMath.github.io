---
layout: default
title: 第7周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 7
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

# 第7周作业

习题三，第15、18、19（2）、23、24、29

# 解答

## 第15题

$[-1,1]$ 上的 $n$ 次 Chebyshev 插值多项式的结点由

$$z_j=\cos\dfrac{(2j+1)\pi}{2(n+1)}$$

给出．而在区间 $[1,2]$ 上，需要先从 $[-1,1]$ 通过仿射坐标变换变成 $[1,2]$，得到

$$x_j=\dfrac{(b-a)z_j}{2}+\dfrac{b+a}{2},$$

然后求出 $f(x)$ 在 $\lbrace x_j\rbrace$ 处的 Lagrange 插值多项式即可．答案：

$p_2(x)=-0.2320x^2+1.3823x-1.1459$

## 第18题

本题和第19(2)题都是求解讲义上的法方程组(3.4.5)．答案：

$p(x)=\dfrac{4}{15}+\dfrac{4}{5}x$

## 第19(2)题

答案：

$p_1(x)=20\ln 2-\dfrac{29}{2}+(9-12\ln 2)x$．

## 第23题

利用讲义的(3.4.12)和(3.4.13)式．确保计算无误！答案：

$1-\dfrac{\pi}{2}+\sum\limits_{j=1}^{\infty}\dfrac{2}{j^2\pi}((-1)^{j-1}+1)T_j(x)$．

## 第24题

利用讲义的法方程组，即(3.5.2)式求解即可．答案为

$y=-\dfrac{7}{10}+\dfrac{11}{10}x$．


## 第29题

设经过 $\lbrace(x_i,y_i)\rbrace_{i=1}^{m}$ 的 Lagrange 插值多项式为

$$p(x)=a_0+a_1x+\cdots+a_{m-1}x^{m-1}$$ 

则 $p(x)$ 的均方误差是

$$\mathcal{L}(a_0,a_1,\cdots,a_{m-1})=\dfrac{1}{m}\sum\limits_{i=1}^m(p(x_i)-y_i)^2=0.$$

所以 $p(x)$ 也是最小二乘拟合函数．



