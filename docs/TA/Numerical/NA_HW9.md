---
layout: default
title: 第9周作业
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

# 第9周作业

教材习题5：5、6

# 解答

## 第5题

{: .problem}
> 设函数 $f(x)$ 在区间 $[a,b]$ 上有二阶连续导数．证明
>
> $$\int_a^bf(x)\mathrm{d}x=(b-a)f\left(\dfrac{a+b}{2}\right)+\dfrac{(b-a)^3}{24}f^{\prime\prime}(\xi), \quad \xi\in(a,b).$$

**证明：** 由泰勒展开，

$$f(x)=f(\dfrac{a+b}{2})+(x-\dfrac{a+b}{2})f'(\dfrac{a+b}{2})+\dfrac{1}{2}(x-\dfrac{a+b}{2})^2f^{\prime\prime}(\eta).$$

其中 $\eta\in(a,b)$．两边在区间 $(a,b)$ 上积分，并用积分中值定理，即得结论．

## 第6题

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







