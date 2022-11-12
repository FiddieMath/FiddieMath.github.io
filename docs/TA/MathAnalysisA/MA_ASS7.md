---
layout: default
title: 第7次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 11
---

访问次数：
<script src="https://sinacloud.net/egg-lib/hit-kounter/hit-kounter-lc-0.4.1.js"></script>
<span data-hk-page="current"> - </span>


## 第7次作业

习题3.4/15, 16, 18. 

习题3.5/1, 3, 4.

## 主要问题

### 3.4/15题

{: .problem}
> **问题1：** 用反证法证明$f(x)$具有单调性. 若不然, 存在$x_0\in\mathbb{R}$, 存在$\delta_1>0$,
> 使得$f(x)$在$(x_0-\delta_1,x_0)$与$(x_0,x_0+\delta_1)$中具有相反的单调性.

错误原因：存在连续函数, 在任意子区间都不单调.

{: .problem}
> **问题2：** 依题意, 若$f(x)$存在, 则$\lim\limits_{x\to -\infty}f(f(x))=+\infty$. 
> 则由14题可知, $\lim\limits_{x\to-\infty}f(x)=+\infty$. 

错误原因：14题说的是$\lim\limits_{x\to \infty}f(f(x))=\infty$可以推出$\lim\limits_{x\to\infty}f(x)=\infty$. 
而$\lim\limits_{x\to\infty}f(x)=\infty$的定义为(参见书的第47页和51页):

- 对任意$M>0$, 存在$K>0$, 当$\vert x\vert >K$时, $\vert f(x)\vert >M$. 

这里双边都要趋于无穷（正无穷或负无穷）.

{: .problem}
> **问题3：** 只讨论了$f$严格递增和严格递减就说这样的$f$不存在.

错误原因：没有排除$f$同时递增或递减的情况.



### 3.4/16题

{: .problem}
> **问题1：** 推出$\sum\limits_{k=0}^{n-1}g\left(\dfrac{k}{n}\right)=f(0)-f(1)=0$后, 
> 说“假设$\forall x\in \left[0,1-\dfrac{1}{n}\right]$, $g(x)\ne 0$”然后导出矛盾. 

错误原因：不能这样假设, 假设的条件过强, 应该假设“$g\left(\dfrac{k}{n}\right)$全为正或全为负”. 

### 3.4/18题

{: .problem}
> **问题1：** 取$c\in[a,+\infty)$, 则$f\in C^0[a,c]$. 由于$\dfrac{f(x)}{x}$是$[a,c]$上的连续函数,
> 而闭区间上的连续函数是一致连续的, 此时若让$c\to+\infty$, 那么也就说$\dfrac{f(x)}{x}$为$[a,+\infty)$中的一致连续函数.

错误原因：只能说明对任意$c\in[a,+\infty)$, 函数$\dfrac{f(x)}{x}$是$[a,c]$上的连续函数(这是所谓的“内闭一致连续”),
但不能说明在$[a,+\infty)$上一致连续. 

例如：函数$g(x)=\sin(x^2)$在所有闭区间$[a,c]$都是一致连续的, 但是在$[a,+\infty)$上不是一致连续的.

{: .problem}
> **问题2：** 证明的时候, 写$\varepsilon>0$, $\exists \delta=\dfrac{\varepsilon}{B}$(其中$B$是跟$x,y$有关的), 
> 当$\vert x-y\vert  < \delta$时, $\left\vert \dfrac{f(x)}{x}-\dfrac{f(y)}{y}\right\vert  \le B\vert x-y\vert  < \varepsilon.$

错误原因：取的$\delta$必须跟$x,y$无关, 只能是个常数($a$也是常数, 所以可以跟$a$有关). 请回顾一致连续的定义.

### 3.5/3题

{: .problem}
> **问题1：** 证后半部分的时候, 作分割$a=x_0 < x_1 < x_2 < \cdots < x_n = b$. 
> 假设$f$不恒为$0$, 且$\int_a^bf=0$, 则存在$x_m$($m\in\lbrace 0,1,\cdots,n\rbrace$), 使得$f(x_m)>0$. 

错误原因: 有可能会出现$f(x_0)=f(x_1)=\cdots=f(x_n)=0$但$f$不恒为0, 且$\int_a^bf=0$的情况. 

> **问题2：** 证后半部分的时候, 用保号性时没把“$>$”取极限后变成“$\ge$”.

错误原因：强调过$N$遍的问题了，还是有同学没注意= =莫得办法

### 3.5/4题

{: .problem}
> **问题1：** 讨论了一大堆$x > y$, $x < y$等等.

请同学们善于用绝对值, 这题其实两三行就能搞定. (虽然讨论也没错, 但是就是不太符合数学分析的taste)

{: .problem}
> **问题2：** 写$\int_c^{x_1}f(t)\mathrm{d}t-\int_c^{x_2}f(t)\mathrm{d}t=\int_c^{x_1-x_2}f(t)\mathrm{d}t$. 

拜托, 积分的四则运算性质不是这么用的!



## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.** 设$a>0$. 若$f\in \mathrm{Lip}([a,+\infty))$, 证明：存在常数$M>0$, 使得

$$\vert f(x)-f(a)\vert \le Mx.$$

**3.** 证明：如果$f(x)$是连续的, 并且

$$f(x)=\int_0^xf(t)\mathrm{d}t,$$

则$f(x)$恒为零. 

**4.** (1)设$f\in \mathrm{Lip}([0,1])$, 即存在常数$M>0$满足

$$\vert f(x)-f(y)\vert \le M\vert x-y\vert , \qquad \forall x,y\in[0,1].$$

证明: 对于任意正整数$n$, 

$$\left\vert \int_0^1f(x)\mathrm{d}x-\dfrac{1}{n}\sum\limits_{k=1}^nf\left(\dfrac{k}{n}\right)\right\vert 
< \dfrac{M}{2n}.$$

(2)如果$f\in C^0([0,1])$, 能否证明存在常数$C>0$使得对于任意正整数$n$, 有

$$\left\vert \int_0^1f(x)\mathrm{d}x-\dfrac{1}{n}\sum\limits_{k=1}^nf\left(\dfrac{k}{n}\right)\right\vert 
= \dfrac{C}{n}?$$
