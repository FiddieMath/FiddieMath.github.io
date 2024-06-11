---
layout: default
title: 第10周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 10
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

# 第10周作业

教材习题5：13、15

# 解答

## 第13题

{: .problem}
> 设 $n$ 为偶数．证明
>
> $$S_{\frac{n}{2}}(f)=\dfrac{1}{3}[4T_n(f)-T_{\frac{n}{2}}(f)].$$
>
> 其中，
>
> $$S_m(f)=\dfrac{h}{3}\Big[f(a)+f(b)+4\sum\limits_{i=1}^mf(a+(2i-1)h)+2\sum\limits_{i=1}^{m-1}f(a+2ih)\Big],$$
>
> $$T_n(f)=\dfrac{h}{2}\Big[f(a)+f(b)+2\sum\limits_{i=1}^{n-1}f(a+ih)\Big]$$
>
> $h=\dfrac{b-a}{2m}=\dfrac{b-a}{n}$．

**证明：** 

以下统一取 $h=\dfrac{b-a}{n}$．则

$$S_{\frac{n}{2}}(f)=\dfrac{h}{3}\Big[f(a)+f(b)+4\sum\limits_{i=1}^{\frac{n}{2}}f(a+(2i-1)h)+2\sum\limits_{i=1}^{\frac{n}{2}-1}f(a+2ih)\Big],$$

$$T_n(f)=\dfrac{h}{2}\Big[f(a)+f(b)+2\sum\limits_{i=1}^{n-1}f(a+ih)\Big]$$

$$T_{\frac{n}{2}}(f)=h\Big[f(a)+f(b)+2\sum\limits_{i=1}^{\frac{n}{2}-1}f(a+2ih)\Big]$$

比较以下它们各项的系数：

$$\begin{array}{|c|c|c|c|c|c|c|c|c|}
\hline  & f(a) & f(a+h) & f(a+2h) & f(a+3h) & f(a+4h) &  \cdots &  f(b) \\
\hline S_{\frac{n}{2}} & \dfrac{h}{3} & \dfrac{4h}{3} & \dfrac{2h}{3} & \dfrac{4h}{3} & \dfrac{2h}{3} & \cdots & \dfrac{h}{3} \\
\hline T_n(f)            & \dfrac{h}{2} & h & h & h & h &\cdots & \dfrac{h}{2} \\
\hline T_{\frac{n}{2}}(f) & h & 0 & 2h & 0 & 2h & \cdots & h \\ \hline
\end{array}$$

于是，在 $\dfrac{1}{3}(4T_n(f)-T_{\frac{n}{2}}(f))$ 中，

$f(a)$ 和 $f(b)$ 的系数为 $\dfrac{1}{3}(4\cdot\dfrac{h}{2}-h)=\dfrac{h}{3}$，等于 $S_{\frac{n}{2}}(f)$ 中 $f(a)$，$f(b)$ 的系数；

$f(a+(2i-1)h)$ 的系数为 $\dfrac{1}{3}(4\cdot h+0) =\dfrac{4h}{3}$，等于 $S_{\frac{n}{2}}(f)$ 中 $f(a+(2i-1)h)$ 的系数；

$f(a+2ih)$ 的系数为 $\dfrac{1}{3}(4h-2h) = \dfrac{2h}{3}$，等于 $S_{\frac{n}{2}}(f)$ 中 $f(a+2ih)$ 的系数．

综上，

$$S_{\frac{n}{2}}(f)=\dfrac{1}{3}[4T_n(f)-T_{\frac{n}{2}}(f)].$$

## 第15题

{: .problem}
> 试在 Euler-Maclaurin 公式 (4.2) 中令 $[a,b]=[0,n]$，$h=1$，推导出公式
>
> $$\begin{aligned}
\sum_{j=0}^nf(j)&=\int_0^nf(x)\mathrm{d}x+\dfrac{1}{2}[f(0)+f(n)]+\dfrac{1}{12}[f'(n)-f'(0)] \\
&\qquad -\dfrac{1}{720}[f^{\prime\prime\prime}(n)-f^{\prime\prime\prime}(0)]
-\sum\limits_{i=1}^n\int_0^1f^{(4)}(i-1+t)q_4(t)\mathrm{d}t,
\end{aligned}$$
>
> 以及计算 
>
> $$\sum\limits_{j=1}^n j,\qquad \sum\limits_{j=1}^nj^2, \qquad \sum\limits_{j=1}^nj^3$$
>
> 的公式．

在 (4.2) 中，令 $[a,b]=[0,n]$，$h=1$，则

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


