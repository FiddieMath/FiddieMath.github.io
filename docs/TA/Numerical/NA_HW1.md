---
layout: default
title: 第1周作业+答疑
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 1
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

# 第 1 周作业（理论1）

讲义第一章1、3、4、5

**1．** 应用梯形公式

$$T=\dfrac{b-a}{2}(f(a)+f(b))$$

计算积分

$$I=\int_0^1\mathrm{e}^{-x}\mathrm{d}x$$

的近似值，在整个计算过程中按四舍五入规则取五位小数．计算中产生的误差的主要原因是离散或是舍入？为什么？

**3．** 证明：若近似数 $\overline{a}=\pm a_0a_1\cdots a_m.a_{m+1}\cdots a_na_{n+1}\cdots a_{n+r}(r\in\mathbb{N})$ 的相对误差有估计式

$$\left\vert\dfrac{a-\overline{a}}{\overline{a}}\right\vert \le \dfrac{1}{2(a_s+1)}\times 10^{-(n-s)},$$

其中 $a_s\ne 0$ 是 $\overline{a}$ 的第一位有效数字，则 $\overline{a}$ 至少具有 $n+1-s$ 位有效数字．

**4．** 设 $\overline{x}=23.3123$，$\overline{y}=23.3122$，且 $\vert e_{\overline{x}}\vert \le \dfrac{1}{2}\times 10^{-4}$，$\vert e_{\overline{y}}\vert \le \dfrac{1}{2}\times 10^{-4}$．问差 $\overline{x}-\overline{y}$ 最多有几位有效数字？

**5．** 当 $x(>0)$ 很大时，如何计算 (1) $\arctan(x+1)-\arctan x$；(2) $\ln(x-\sqrt{x^2-1})$；(3) $\dfrac{\tan x}{x-\sqrt{x^2-1}}$，可使其误差较小？

# 解答

### 第1题解答

舍入误差在这里对结果的影响不算大，产生误差应该主要是把连续积分问题离散化造成的．

在后续课程会学习数值积分，涉及到各种数值积分公式，将会从理论上分析离散误差的上界．

### 第3题解答

提示：讨论 $s=0$ 或 $s\ne 0$，验证有效数字的定义即可．

思考：如果 $r=0$，这题能不能说 $\overline{a}$ 恰好有 $n+1-s$ 位有效数字？

### 第4题解答

记 $\overline{z}=\overline{x}-\overline{y}=0.0001$，且

$$\begin{aligned}
\vert e_{\overline{z}}\vert &=\vert e_{\overline{x}}-e_{\overline{y}}\vert \\
&\le \vert e_{\overline{x}}\vert+\vert e_{\overline{y}}\vert \le 1\times 10^{-4}, 
\end{aligned}$$

其中 $\overline{z}=z_0z_1\cdots z_m.z_{m+1}\cdots z_n$ 满足：$m=0$，$n=4$，$s=4$．
因此，$\overline{x}-\overline{y}$ 最多有 1 位有效数字．




### 第5题解答

(1) $\arctan(x+1)-\arctan x=\arctan\dfrac{1}{1+x+x^2}$．

(2) $\ln(x-\sqrt{x^2-1})=-\ln(x+\sqrt{x^2-1})$．

(3) $\dfrac{\tan x}{x-\sqrt{x^2-1}} = (x+\sqrt{x^2+1})\tan x$．


# 答疑

### 1．浮点数运算的次序问题

上课提到，计算机计算机器数时，先正确地进行计算，然后再进行规格化和舍入，最后以机器数的形式存储在存储器中．
具体而言，对于两个机器数$x$，$y$，记$\odot$表示加、减、乘、除的其中一个运算，当$x\odot y$被计算和存储时，我们得到的最接近于$x\odot y$的数实际上是以一个舍入到$fl(x\odot y)$机器数的形式拟合$x\odot y$，然后存储那个数．

浮点数运算满足下面的不等式：

$$fl(x\odot y)=(x\odot y)(1+\delta), \qquad |\delta|\le\varepsilon.$$

其中$\varepsilon$是机器精度．

{: .problem}
> 机器数$x=0.31426\times 10^{3}$，$y=0.92577\times 10^5$，在$p=10$的计算机、浮点数系采用$t=5$，计算两个机器数的加减乘除的值．

对中间结果用双倍长的累加器，我们有

$$\begin{aligned}
x+y&=0.9289126000\times 10^5, \\
x-y&=-0.9226274000\times 10^5, \\
x\ast y&=0.2909324802\times 10^8, \\
x\div y&\approx 0.3394579647\times 10^{-2}, 
\end{aligned}$$

有5位小数的计算机以舍入形式存储它们：

$$\begin{aligned}
fl(x+y)&=0.92891\times 10^5, \\
fl(x-y)&=-0.92263\times 10^5, \\
fl(x\ast y)&=0.29093\times 10^8, \\
fl(x\div y)&=0.33946\times 10^{-2}, 
\end{aligned}$$


某同学问了如下问题：

{: .problem}
> 请问这种情况是先舍入还是先左移呢？
>
> 例如：两个机器数$x=0.10245\times 10^{-2}$，$y=0.14763\times 10^{-3}$，$p=10$，$t=5$，于是
> 
> $$\begin{aligned}
x \ominus y&=0.10245\times 10^{-2} - 0.14763\times 10^{-3} \\
&=0.10245\times 10^{-2}-0.014763\times 10^{-2} \\
&=0.087687\times 10^{-2}
\end{aligned}$$
>
> 最后得到$0.08769\times 10^{-2}=0.87690\times 10^{-3}$还是$0.87687\times 10^{-3}$？

根据前面所说的计算步骤，应当先计算出

$$x - y=0.087687\times 10^{-2},$$

然后再取浮点数，根据浮点数满足的不等式（其实就是要对阶），可知

$$x\ominus y = fl(x - y)=0.87687\times 10^{-3}.$$

总之，浮点数运算先对阶，再计算，再舍入(或截断)，得到的结果再对阶．

{: .remark}
> 林成森《数值计算方法》中讲到的浮点数运算是不对的．
> 如果按照林成森《数值计算方法》的浮点数运算，在进行浮点数运算时要先对阶，再舍入（或截断），然后再计算．
> 
> 对阶之后，$y$变成$0.014763\times 10^{-2}$，然后再舍入，变成$0.01476\times 10^{-2}$．所以应该计算的是
> 
> $$\begin{aligned}
x\ominus y&=0.10245\times 10^{-2} - 0.01476\times 10^{-2} \\
&=0.10245\times 10^{-2}-0.01476\times 10^{-2} \\
&=0.08769\times 10^{-2}.
\end{aligned}$$



### 2．相减相消补充

相减相消(catastrophic cancellation)的问题通常都是在不经意中出现的．例如同学们可以考虑在计算机实现泰勒展开：

$$\mathrm{e}^x=\sum\limits_{n=0}^{\infty}\dfrac{x^n}{n!}$$

这个级数对所有$x\in\mathbf{R}$都收敛．在Python中可以如下实现级数计算：

```python
def my_exp(x):
    ans = 1.0;  term = 1.0;     n = 0
    while ans+term != ans: # continue adding new terms until the answer doesn't change
        n = n+1
        term = term * (x/n)
        ans = ans+term
    return ans
```

{: .remark}
> 当$n$充分大时，$x^n/n!$很小，当它的绝对值小于机器精度时，它在计算机中就表示为0，从而后续的项都为0．

对比``my_exp(x)``和``math.exp(x)``结果如下：

| ``x``        | ``my_exp(x)``     | ``math.exp(x)`` |
|:-------------|:------------------|:------|
| 40 | 2.353852668370201e+17 | 2.353852668370200e+17 | 
| 20 | 4.851651954097905e+08 | 4.851651954097903e+08 | 
| 1  | 2.718281828459046e+00 | 2.718281828459045e+00 | 
| -1 | 3.678794411714424e-01 | 3.678794411714423e-01 | 
|-20 | 6.147561828914626e-09 | 2.061153622438558e-09 | 
|-40 | 3.116951588217358e-01 | 4.248354255291589e-18 |

可以看到在多数情况下都是准确的，但是如果是较大的负数($x=-20,-40$)，得到的结果就不准确．
主要是因为当$x>0$时，求和中的所有项都是正的，当$x < 0$时，求和中的项正负交替出现，容易出现相减相消．

为了避免这个问题，当$x < 0$时可以不采用Taylor公式来计算$\mathrm{e}^x$，而是利用恒等式

$$\mathrm{e}^{-x}=\dfrac{1}{\mathrm{e}^x}$$

把$x < 0$转化成$x>0$的情形再进行计算．

```python
def my_exp2(x):
    # Calculation of exp(x), avoiding catastrophic cancellation
    if x >= 0.0:
        return my_exp(x)
    else:
        return 1.0 / my_exp(-x)
```

对比``my_exp2(x)``和``math.exp(x)``结果如下：

| ``x``        | ``my_exp2(x)``     | ``math.exp(x)`` |
|:-------------|:------------------|:------|
| 40 | 2.353852668370201e+17 | 2.353852668370200e+17 | 
| 20 | 4.851651954097905e+08 | 4.851651954097903e+08 | 
| 1  | 2.718281828459046e+00 | 2.718281828459045e+00 | 
| -1 | 3.678794411714423e-01 | 3.678794411714423e-01 | 
|-20 | 2.061153622438557e-09 | 2.061153622438558e-09 | 
|-40 | 4.248354255291587e-18 | 4.248354255291589e-18 |

这样得到的计算结果就非常准确了，达到了15位有效数字．







