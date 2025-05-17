---
layout: default
title: 第10、11周作业（理论9） 
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 9
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

# 第 10、11 周作业（理论9）

第四章 2、3、8、11、16、18、22、23(2)、26

# 解答

### 第2题解答

{: .problem}
>  求 $x_1,x_2$ 使得计算积分 $\displaystyle I(f)=\int_{-1}^1f(x)\mathrm{d}x$ 的求积公式
>
> $$I_2(f)=\dfrac{1}{3}[f(-1)+2f(x_1)+3f(x_2)]$$
>
> 的代数精度至少为 2．

依题意，当 $f(x)=1,x,x^2$ 时求积公式精确地成立．所以有方程组

$$\left\lbrace
\begin{aligned}
&0=\dfrac{1}{3}[-1+2x_1+3x_2], \\
&\dfrac{2}{3}=\dfrac{1}{3}[1+2x_1^2+3x_2^2],
\end{aligned}
\right.$$

解得 $x_1=\dfrac{1\pm \sqrt{6}}{5}$，$x_2=\dfrac{3\mp 2\sqrt{6}}{15}$．

**【易错警示】** 有同学只写了一组解．

### 第3题解答

{: .problem}
> 已知计算积分 $\displaystyle I(f)=\int_{-1}^1f(x)\mathrm{d}x$ 的求积公式
>
> $$I_2(f)=C[f(x_1)+f(x_2)+f(x_3)]$$
>
> 的代数精度是 3，求 $C,x_1,x_2,x_3$．

依题意，当 $f(x)=1,x,x^2,x^3$ 时求积公式精确地成立，所以有方程组

$$\left\lbrace
\begin{aligned}
&2=3C, \\
&0=C(x_1+x_2+x_3), \\
&\dfrac{2}{3}=C(x_1^2+x_2^2+x_3^2), \\
&0=C(x_1^3+x_2^3+x_3^3),
\end{aligned}
\right.$$

整理得 $C=\dfrac{2}{3}$ 且

$$\left\lbrace
\begin{aligned}
&x_1+x_2+x_3=0, \\
&x_1^2+x_2^2+x_3^2=1, \\
&x_1^3+x_2^3+x_3^3=0.
\end{aligned}
\right.$$

下面给出求解方程组

$$\left\lbrace
\begin{aligned}
&x_1+x_2+x_3=p, \\
&x_1^2+x_2^2+x_3^2=q, \\
&x_1^3+x_2^3+x_3^3=r.
\end{aligned}
\right.$$

的一般方法．

设 $x_1,x_2,x_3$ 是三次方程 $x^3+ax^2+bx+c=0$ 的三个根．则

$$\left\lbrace
\begin{aligned}
&-(x_1+x_2+x_3)=a, \\
&x_1x_2+x_2x_3+x_3x_1=b, \\
&x_1x_2x_3=c,
\end{aligned}
\right.$$

其中，

$$\begin{aligned}
x_1^2+x_2^2+x_3^2&=(x_1+x_2+x_3)^2-2(x_1x_2+x_2x_3+x_3x_1) \\
&=a^2-2b.
\end{aligned}$$

且

$$\begin{aligned}
x_1^3+x_2^3+x_3^3 &= -a(x_1^2+x_2^2+x_3^2)-b(x_1+x_2+x_3)-3c \\
&=-a(a^2-2b)+ab-3c = -a^3+3ab-3c.
\end{aligned}$$

所以

$$\left\lbrace
\begin{aligned}
&a=-p, \\
&b=\dfrac{a^2-q}{2}, \\
&c=\dfrac{-a^3+3ab-r}{3}.
\end{aligned}
\right.$$

这就给出了 $x_1,x_2,x_3$ 所满足的三次方程．

现在，$p=0$，$q=1$，$r=0$．所以 $a=0$，$b=-\dfrac{1}{2}$，$c=0$，所以 $x_1,x_2,x_3$ 是方程

$$x^3-\dfrac{1}{2}x=0$$

的三个根，直接解出 $x_1=-\dfrac{\sqrt{2}}{2}$，$x_2=0$，$x_3=\dfrac{\sqrt{2}}{2}$．


### 第8题解答

{: .problem}
> 导出 $n=1,2,3$ 时，开型 Newton-Cotes 型求积公式．

开型 Newton-Cotes 求积公式以 $x_1,\cdots,x_n$ 为结点，其中

$$a=x_0 < x_1 < \cdots < x_n < x_{n+1}=b,$$

且 $x_i=a+i\cdot\dfrac{b-a}{n+1}$，$i=0,1,\cdots,n+1$．

当 $n=1$ 时，得到中点法则：$I_1(f)=(b-a)f\left(\dfrac{a+b}{2}\right)$．

当 $n=2$ 时，得到 $I_2(f)=\dfrac{b-a}{2}\left(f\left(\dfrac{2a+b}{3}\right)+f\left(\dfrac{a+2b}{3}\right)\right)$．

当 $n=3$ 时，得到 $I_3(f)=\dfrac{b-a}{3}\left(2f(\dfrac{3a+b}{4})-f(\dfrac{a+b}{2})+2f(\dfrac{a+3b}{4})\right)$．


### 第11题解答


{: .problem}
> 设函数 $f(x)$ 在 $[-h,h]$ 上充分可导．试推导求积公式
>
> $$\int_0^hf(x)\mathrm{d}x\approx\dfrac{h}{2}[3f(0)-f(-h)]$$
>
> 的余项．

$f(x)$ 在 $x=0$ 和 $x=-h$ 处的插值多项式为

$$p(x)=f(0)\dfrac{x+h}{0+h} + f(-h)\dfrac{x-0}{-h-0} = \dfrac{1}{h}f(0)(x+h) - hf(-h)x.$$

两边积分，得

$$\int_0^hf(x)\mathrm{d}x\approx \int_0^hp(x)\mathrm{d}x
= \dfrac{h}{2}[3f(0)-f(-h)].$$

由插值多项式误差公式，

$$f(x)-p(x)=\dfrac{1}{2}f^{\prime\prime}(\xi_x)\cdot x(x+h),$$

两边积分，并用积分中值定理，得余项为

$$\int_0^h[f(x)-p(x)]\mathrm{d}x=f^{\prime\prime}(\xi)\cdot \dfrac{1}{2}\int_0^hx(x+h)\mathrm{d}x
=\dfrac{5}{12}h^3f^{\prime\prime}(\xi).$$



### 第16题解答

{: .problem}
>  用复合梯形公式计算积分 $\displaystyle I(f)=\int_1^2\dfrac{1}{2x}\mathrm{d}x$．要求误差不超过 $10^{-3}$，并把计算得结果与准确值 $I(f)$ 比较．

复合梯形公式的误差余项是 $-\dfrac{h^2(b-a)}{12}f^{\prime\prime}(\xi)$，其中 $h$ 是每个小区间长度，$b-a=2-1=1$，$f^{\prime\prime}(x)=\dfrac{1}{x^3}$，只需让

$$\dfrac{h^2}{12} \le 10^{-3},$$

可取 $h=0.1$，即分成 10 个区间．利用 MATLAB 验证所得数值积分公式的结果可发现误差确实是小于 $10^{-3}$．（有同学算出 $3.2\times 10^{-4}$ ）

### 第18题解答

{: .problem}
>  用复合 Simpson 公式计算积分 $\displaystyle I(f)=\int_1^23\ln x \mathrm{d}x$．要求误差不超过 $10^{-5}$，并把计算得结果与准确值 $I(f)$ 比较．

复合 Simpson 公式的误差余项是 $-\dfrac{h^4(b-a)}{180}f^{(4)}(\xi)$，其中 $h$ 是每个小区间长度，$b-a=2-1=1$，$f^{(4)}(x)=-\dfrac{18}{x^4}$，只需让

$$\dfrac{h^4}{180}\times 18 \le 10^{-5},$$

可取 $h=0.1$，即分成 10 个区间．利用 MATLAB 验证所得数值积分公式的结果可发现误差确实是小于 $10^{-5}$．（有同学算出 $2.87\times 10^{-6}$ ）

### 第22题解答

{: .problem}
> 在 Euler-Maclaurin 公式 (4.4.6) 中令 $[a,b]=[0,n]$，$h=1$，推导出公式
>
> $$\sum\limits_{j=0}^nf(j)=\int_0^nf(x)\mathrm{d}x+\dfrac{1}{2}[f(0)+f(n)]+\dfrac{1}{12}[f'(0)-f'(0)]-\dfrac{1}{720}[f^{(3)}(n)-f^{(3)}(0)]-\sum\limits_{i=1}^n\int_0^1f^{(4)}((i-1+t)h)q_4(t)\mathrm{d}t.$$
>
> 以及计算 $\sum\limits_{j=1}^nj$，$\sum\limits_{j=1}^nj^2$，$\sum\limits_{j=1}^nj^3$ 的公式．

在 (4.4.6) 中，令 $[a,b]=[0,n]$，$h=1$，则

$$I(f)=\int_0^nf(x)\mathrm{d}x,$$

$$\begin{aligned}
T_n(f)&=\dfrac{h}{2}\Big[f(a)+f(b)+2\sum\limits_{i=1}^{n-1}f(a+ih)\Big] \\
&=\dfrac{1}{2}\Big[f(0)+f(n)+2\sum\limits_{j=1}^{n-1}f(j)\Big] \\
&=\sum\limits_{j=0}^nf(j) - \dfrac{1}{2}[f(0)+f(n)].
\end{aligned}$$

$$q_2(0)=\dfrac{1}{12}, \qquad q_4(0)=-\dfrac{1}{720},$$

展开到 $k=4$，得

$$\begin{aligned}
\int_0^nf(x)\mathrm{d}x&=\sum\limits_{j=0}^nf(j) - \dfrac{1}{2}[f(0)+f(n)]
-\dfrac{1}{12}[f'(n)-f'(0)]   \\
&\qquad -\dfrac{1}{720}[f^{\prime\prime\prime}(n)-f^{\prime\prime\prime}(0)]
+\sum\limits_{i=1}^n\int_0^1f^{(4)}(i-1+t)q_4(t)\mathrm{d}t.
\end{aligned}$$

稍作移项可得欲证式子．

① 令 $f(x)=x$，得

$$\dfrac{1}{2}n^2=\sum\limits_{j=0}^nj-\dfrac{1}{2}n,$$

即

$$\sum\limits_{j=1}^nj=\dfrac{1}{2}(n^2+n)=\dfrac{1}{2}n(n+1).$$

② 令 $f(x)=x^2$，得

$$\dfrac{1}{3}n^3=\sum\limits_{j=0}^nj^2-\dfrac{1}{2}n^2-\dfrac{1}{12}\cdot 2n,$$

整理得

$$\sum\limits_{j=1}^nj^2=\dfrac{1}{6}(2n^3+3n^2+n)=\dfrac{1}{6}n(n+1)(2n+1).$$

③ 令 $f(x)=x^3$，得

$$\dfrac{1}{4}n^4=\sum\limits_{j=0}^nj^3-\dfrac{1}{2}n^3-\dfrac{1}{12}\cdot 3n^2,$$

整理得

$$\sum\limits_{j=1}^nj^3=\dfrac{1}{4}(n^4+2n^3+n^2)=\dfrac{1}{4}n^2(n+1)^2.$$



### 第23(2)题解答

{: .problem}
> 用 Romberg 积分法计算下列积分的近似值 $T_{3,3}$： $\int_0^1x^2\mathrm{e}^x\mathrm{d}x$，并与积分准确值 比较．

计算得 

$T_{1,1}=\frac{\mathrm{e}}{2}$，$T_{2,1}=\frac{1}{4}(\mathrm{e}+\frac{\mathrm{e}^{1/2}}{2})$，$T_{3,1} = \frac{1}{8}(\mathrm{e}+\frac{\mathrm{e}^{1/4}}{8}+\frac{\mathrm{e}^{1/2}}{2}+\frac{9\mathrm{e}^{3/4}}{8})$，

$T_{2,2}=\frac{1}{6}(\mathrm{e}+\mathrm{e}^{1/2})$，$T_{3,2}=\frac{1}{48}(4\mathrm{e}+\mathrm{e}^{1/4}+2\mathrm{e}^{1/2}+9\mathrm{e}^{3/4})$，

$T_{3,3}=\frac{7}{90}\mathrm{e}+\frac{1}{30}\mathrm{e}^{1/2}+\frac{1}{45}\mathrm{e}^{1/4}+\frac{1}{5}\mathrm{e}^{3/4}=0.718313197$．

准确值：$\displaystyle \int_0^1x^2\mathrm{e}^x\mathrm{d}x = \mathrm{e}-2=0.718281828\cdots$，

$$\left\vert\int_0^1x^2\mathrm{e}^x\mathrm{d}x-T_{3,3}\right\vert < 3.137 \times 10^{-5}.$$



### 第26题解答

{: .problem}
> 证明：$T_{j,j}=\alpha_1 T_{1,1}+\alpha_2 T_{2,1} + \cdots + \alpha_jT_{j,1}$，其中 $\alpha_1+\cdots+\alpha_j=1$，$j\ge 2$．

Romberg 法的迭代公式为

$$T_{m,j}=T_{m,j-1}+\dfrac{1}{4^{j-1}-1}(T_{m,j-1}-T_{m-1,j-1}), \quad j=2,3,\cdots(m\ge j).$$

因为 Romberg 积分表中每一项都写成该项左侧与左上方项的系数和为 1 的线性组合，所以反复上式代入 $T_{j,j}$ 的表达式，一直进行下去就能得到 $T_{j,j}$ 可以写成 $T_{1,1},\cdots,T_{j,1}$ 的系数和为 1 的线性组合．





