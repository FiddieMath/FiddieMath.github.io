---
layout: default
title: 第12周作业
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 12
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

# 第12周作业

教材习题10：1、3

# 解答

## 第1题


{: .problem}
> 求微分方程初值问题
>
> $$\dfrac{\mathrm{d}y}{\mathrm{d}t}=\alpha y-\beta y^2, \qquad y(t_0)=y_0$$
>
> 的解 $y(t)$，并证明 $\lim\limits_{t\to\infty}y(t)=\dfrac{\alpha}{\beta}$．

利用分离变量法（复习《常微分方程》），可得

$$y(t)=\dfrac{\alpha}{\beta-C\mathrm{e}^{-\alpha t}},$$

代入 $y(t_0)=y_0$ 可解得 $C$，从而

$$y=\dfrac{\alpha y_0}{\beta y_0-(\beta y_0-\alpha)\mathrm{e}^{-\alpha(t-t_0)}}.$$

让 $t\to+\infty$，得 $\lim\limits_{t\to+\infty}y(t)=\dfrac{\alpha}{\beta}$．

## 第3题


{: .problem}
> 假设函数 $g(x)$ 和 $h(x)$ 在区间 $[a,b]$ 上连续，证明初值问题
>
> $$y'=g(x)y+h(x), \qquad y(a)=\eta$$
>
> 在 $[a,b]$ 上有唯一解，并且对任何初始值都是适定的．

存在唯一性：直接使用 10.1 节定理 1．

适定性：直接使用 10.1 节定理 2．








