---
layout: default
title: 第9次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 15
---

## 第9次作业

习题4.1/17(2)(4)(6), 19(2), 21.

习题4.2/2(1)(3), 3(1)(3), 5, 7(2), 9, 11, 13.

习题4.3/1,3,4(奇数), 5(奇数)

## 主要问题

还没改，别急

## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.** 设$\mathbf{I}_n$是$n\times n$单位矩阵, $\mathbf{A}$是$n\times n$实矩阵, 
函数$f(x)=\mathrm{det}(\mathbf{I}+x\mathbf{A})$. 计算$f'(0)$的值.

{: .note}
> Legendre多项式在数值计算方法(大二下学期和大三上学期的课)中经常用到. 感兴趣的同学欢迎以后走信息与计算科学方向.

**2.(Legendre多项式)** 考虑多项式函数

$$L_n(x)=\dfrac{1}{2^nn!}\dfrac{\mathrm{d}^n}{\mathrm{d}x^n}(x^2-1)^n, \qquad n\in\mathbb{N}.$$

(1)证明: 对任意$n\ge 1$, 有递推关系式

$$(n+1)L_{n+1}(x)=(2n+1)xL_n(x)-nL_{n-1}(x).$$

(2)求$\mathrm{deg}(L_n(x))$. 

(3)证明: 对任意次数不超过$n-1$次的多项式$P(x)$, 都有

$$\int_{-1}^1L_n(x)P(x)\mathrm{d}x=0.$$

从而推导出当$m\ne n$时, 多项式列$\lbrace L_n(x)\rbrace$满足如下的**正交性质**: 

$$\int_{-1}^1L_m(x)L_n(x)\mathrm{d}x=0.$$

(4)计算

$$\int_{-1}^1(L_n(x))^2\mathrm{d}x.$$

{: .note}
> 第三章(74页)我们证明了Young不等式: 
> 
> $$ab\le\dfrac{a^p}{p}+\dfrac{b^q}{q},$$ 
> 
> 其中$a>0, b>0, p>1, q>1$, 并且$p^{-1}+q^{-1}=1$. 
> 我们用积分来给出它的另外一种证明.

**3.** 设$y=f(x)$和$x=g(y)$互为相反数且都是非负、单调递增的可导函数, 
并且$f(0)=g(0)=0$. 证明: 当$x,y\ge 0$时, 

$$xy\le \int_0^xf(t)\mathrm{d}t+\int_0^yg(t)\mathrm{d}t.$$

然后导出Young不等式

$$xy\le\dfrac{1}{p}x^p+\dfrac{1}{q}x^q,$$

其中, $x,y\ge 0$, $p,q>1$满足$p^{-1}+q^{-1}=1$. 

上述不等式等号成立条件是什么？它对应着什么几何意义? 


{: .remark}
> 把“可导”的条件减弱为“连续”, 甚至把“连续”的条件去掉也对, 但是应该是要用到第六章的知识才能证. 
>
> 可以参考[https://handwiki.org/wiki/Integral_of_inverse_functions](https://handwiki.org/wiki/Integral_of_inverse_functions).



&nbsp; 

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

## 思考题提示

**1.** 答案为$\mathrm{tr}(\mathbf{A})$. 

**2.** (1)用Leibniz公式; (3)分部积分$n$次. 
(4)分部积分$n$次, 最后可能要用到Wallis公式, 答案为$\dfrac{2}{2n+1}$. 

**3.** 由恒等式$g(f(x))=x$, 两边同乘$f'(x)$可得$f'(x)g(f(x))=xf'(x)$, 两边作积分.