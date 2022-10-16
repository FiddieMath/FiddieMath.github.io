---
layout: default
title: 第3次作业
parent: 数学分析A
grand_parent: 助教工作
---

## 第3次作业

2.3节/3,7,8,9题; 2.4节/1,4(1),8,9; 2.5节/1,10,11.

### 主要问题

{% raw %}

- 2.3/7(1)题: 有同学直接写
$\sup\lbrace|a_k-a_l|:k,l\ge n\rbrace=\sup\lbrace a_k|k\ge n\rbrace -\inf\lbrace a_l|l\ge n\rbrace$
但这恰好是题目要你证的. 请用$\sup$与$\inf$的定义写清楚.
- 2.3/7(1)题: 有同学写存在$k,l$使得$a_k=\bar{a}_n$与$a_l=\underline{a}_n$, 这是不对的. 
上确界的$\sup$跟最大值的$\max$有本质区别: $\max$一定能取到，但$\sup$不一定能取到.
- 2.3/7(2)题: 只证明了一个方向.
- 2.4/9题: 用了Taylor展开，这是后面的知识，还是请按题目要求用2.4/8题解答.
- 2.5/1题: 没证明唯一性.
- 2.5/10、11题: 没看懂题目含义, 它是假设一个定理成立, 证明另一个定理.
- 2.5/11题: 没用$\varepsilon-N$语言把过程写清楚, 而是直接取极限, 保号性是“$ < $”变成“$\le$”. 

{% endraw %}
### 课后思考题: 

**1.** 设$f(x)$在区间$I$中有界, 证明: 

$$\sup\limits_{x\in I}f(x)-\inf\limits_{x\in I}f(x)=\sup\limits_{x,y\in I}|f(x)-f(y)|.$$

**2.** 证明: 对任意数列$\{a_n\}$, 都有

$$\mathop{\underline{\lim}}\limits_{n\to\infty}\left(1+\dfrac{1}{n}\right)^{a_n}
=e^{\mathop{\underline{\lim}}\limits_{n\to\infty}\frac{a_n}{n}}.$$

**3.** 证明: (Cauchy准则$\Rightarrow$Bolzano定理) 如果$\mathbb{R}$中Cauchy数列必收敛, 则$\mathbb{R}$中有界数列必有收敛子列.

**4.** 证明: (有限覆盖定理$\Rightarrow$Cauchy准则) 如果闭区间的任意开覆盖都有有限子覆盖, 则$\mathbb{R}$中的Cauchy列都是收敛的.