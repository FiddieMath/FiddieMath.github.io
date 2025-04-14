---
layout: default
title: 第8周作业 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 8
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

# 第 8 周作业（理论8）

第三章 27、28

# 解答

### 第27题解答

{: .problem}
>  数据 $\lbrace(x_i,y_i)\rbrace_{i=1}^{m}$ 的最小二乘拟合函数 $p(x)=a_0+a_1x+\cdots+a_{m-1}x^{m-1}$ 恰是经过点集 $\lbrace(x_i,y_i)\rbrace_{i=1}^{m}$ 的 Lagrange 插值多项式．

设经过 $\lbrace(x_i,y_i)\rbrace_{i=1}^{m}$ 的 Lagrange 插值多项式为

$$p(x)=a_0+a_1x+\cdots+a_{m-1}x^{m-1}$$ 

则 $p(x)$ 的均方误差是

$$\mathcal{L}(a_0,a_1,\cdots,a_{m-1})=\dfrac{1}{m}\sum\limits_{i=1}^m(p(x_i)-y_i)^2=0.$$

因此均方误差的最小值为 $0$，并且当均方误差取到最小值时，一定满足插值条件 $p(x_i)=y_i$，$i=1,\cdots,m$．根据 Lagrange 插值多项式的唯一性，$p(x)$ 的最小二乘拟合函数就是 Lagrange 插值多项式．





### 第28题解答

{: .problem}
> 记 $P_2=\mathrm{span}\lbrace 1,x,x^2\rbrace$ 是二次多项式空间，求 $p\in P_2$ 使得
>
> $$\int_0^2(x-1)^2[\vert x-1\vert^3-p(x)]^2\mathrm{d}x$$
>
> 达到最小．

为了计算的方便，可以平移区间 $[0,2]$ 为 $[-1,1]$，只需求 $p\in P_2$ 使得

$$I(a_0,a_1,a_2)=\int_{-1}^1x^2[\vert x\vert^3-p(x+1)]^2\mathrm{d}x$$

达到最小．设 $p(x+1)=a_0+a_1x+a_2x^2$．

当 $I(a_0,a_1,a_2)$ 达到最小的时候， 

$$\dfrac{\partial I}{\partial a_i}=-2\int_{-1}^1x^2\cdot x^i[\vert x\vert^3-(a_0+a_1x+a_2x^2)] = 0$$

其中 $i=0,1,2$，即可建立关于 $a_0,a_1,a_2$ 的线性方程组

$$\begin{bmatrix} \frac{2}{3} & 0 & \frac{2}{5} \\ 0 & \frac{2}{5} & 0 \\ \frac{2}{5} & 0 & \frac{2}{7}\end{bmatrix}\begin{bmatrix} a_0 \\ a_1 \\ a_2 \end{bmatrix}=\begin{bmatrix}\frac{1}{3} \\ 0 \\ \frac{1}{4}\end{bmatrix},$$

学会用 MATLAB 求解：

```
format rat
A = [2/3,0,2/5; 0,2/5,0; 2/5,0,2/7];
b = [1/3;0;1/4];
x = A\b;
```

解得 $a_0=-\frac{5}{32}$, $a_1=0$, $a_2=\frac{35}{32}$．

于是 $p(x)=-\frac{5}{32}+\frac{35}{32}(x-1)^2=\frac{35}{32}x^2-\frac{35}{16}x+\frac{15}{16}$．

**【易错点】** 

（1）不理解最小二乘法达到最小值的必要条件，列出错误的方程．

（2）计算出错，比如 $\int_{-1}^1x^{2+i}\vert x\vert^3\mathrm{d}x=2\int_{0}^1x^{5+i}\mathrm{d}x$ 忘记乘 2 等．











