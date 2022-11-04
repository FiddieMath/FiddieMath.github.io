---
layout: default
title: 第5次作业
parent: 数学分析A
grand_parent: 助教工作
nav_order: 7
---

## 第5次作业

3.1节/6;

3.2节/1(1)(3); 2(1)(3)(5); 3(1)(3)(5); 4(2); 5(1)(3)(5); 8;

3.3节/1(2); 3; 5; 6; 8(1); 9(2); 12.

## 所有同学的作业反馈：

<span style="display:block;color:red;">
由于这次是线上批改，所以同学们有问题的地方我都做了记录，具体反馈请点击[这里](/res/HW5.pdf)下载. 
</span>

{: .remark}
> 1. “学号后三位”如果出现重复，请根据右边的具体反馈(例如截图的字迹等等)判断哪个是自己的作业. 
> 
> 2. 有些同学的反馈在一页之内可能放不完，会出现自动翻页的情况，例如尾号为010、040的同学就是如此. 
>
> 3. 反馈为空白的同学是我没批改到的, 可能是因为同学们没有提交成功. 
> 如果遇到这种情况请重新提交作业(2022年11月4日14:00前提交至另一位助教的邮箱), 逾期不候.
> 大约18:00前我会更新后续提交同学的作业的反馈情况. 



## 主要问题

{% raw %}

### 3.1/6题

**问题1：** 没有证明极限存在，直接写“对$x_n=\sin(x_{n-1})$取极限可得$A=\sin A$, 所以$A=0$.”

需要用单调有界原理证明数列$\lbrace x_n\rbrace$有极限

**问题2：** 证明了$\vert \sin x\vert \le \vert x\vert $.

这个书上已经证明过了, 无需用求导的方式来证(而且这是后面的知识).

### 3.2/5(5)题

**问题：** 算成了$\dfrac{1}{2}$, 但答案是$\dfrac{1}{4}$. 

### 3.2/8题

**问题1：** 记错$o$和$O$记号的定义. 

有同学写了$\lim\limits_{x\to 0}\dfrac{f(2x)-f(x)}{x}=\alpha$, 
或者写$\lim\limits_{x\to 0}\dfrac{f(2x)-f(x)}{x}=0$. 
大$O$记号定义的正确写法是: 

> 存在$M>0$, 存在$\delta>0$, 当$x\in V(0,\delta)$时, 
> 
> $$\left\vert \dfrac{f(2x)-f(x)}{x}\right\vert \le M.$$

**问题2：** 保序性是把小于号变成小于等于号. 

有较多同学写

$$\vert f(x)-f(\tfrac{x}{2^n})\vert \le M\vert x\vert \left(2^{-1}+\cdots+2^{-n}\right) < M\vert x\vert ,$$

然后让$n\to\infty$得到

$$\vert f(x)\vert  < M\vert x\vert .$$

这是错的, 根据极限的保序性会得到$\vert f(x)\vert \le M\vert x\vert $. 

虽然这个只是细节问题, 对本题的解决影响不大, 但是锻炼严谨的数学思考习惯要从细节开始.

**问题3：** 错误的使用$O$.

有同学直接对下面的式子相加：

$$\begin{aligned}
f(2x)-f(x)&=O(x), \\
f(x)-f(\tfrac{x}{2})&=O(x), \\
\vdots & \\
f(\tfrac{x}{2^n})-f(\tfrac{x}{2^{n+1}})&=O(x)
\end{aligned}$$

得到$f(x)-f\left(\dfrac{x}{2^{n+1}}\right)=O(x).$
在取$n\to\infty$之前, 这没错（有限个$O(x)$相加也是$O(x)$）.
但是如果取$n\to\infty$得到$f(x)=O(x)$就错了, 因为这样就变成无限个$O(x)$相加了.

还是要严谨地用$\varepsilon-\delta$语言写清楚.

**问题4：** 根据$f(x)=o(1)(x\to 0)$得到$f(0)=0$. 

题目没说$f$在$0$处连续. 注意函数极限是在“空心邻域”中定义的.

### 3.3/5题：

**问题1：** 错误的绝对值

少部分同学记错绝对值不等式的方向了

$$\vert \vert x\vert -\vert y\vert \vert \le \vert x\pm y\vert \le \vert x\vert +\vert y\vert .$$

或者这样写：如果$\vert x\vert \ge \vert a\vert $, 则

$$\vert \vert x\vert -\vert y\vert \vert  \ge \vert \vert a\vert -\vert y\vert \vert $$

这都是错的！

**问题2：** 消失的绝对值

做不等式放缩的时候不要漏掉绝对值！比如3.3/5题有同学得到单边的不等式

$$\vert f(x)\vert -\vert f(x_0)\vert  < \varepsilon$$

然后说$\vert f(x)\vert $在$x_0$处连续. 这是错的, 还需要证$\vert f(x)\vert -\vert f(x_0)\vert  > -\varepsilon$. 

**问题3：** 奇怪的依赖关系

引入$\varepsilon,\delta$等变量的时候一定要清楚它们相互之间的依赖关系.

<span style="display:block;color:red;">
而且如果前面写了“$\forall \varepsilon>0$”，那么后面就不要再引入一次$\varepsilon$了,
直接写“对上述$\varepsilon$”, 会让你的逻辑清晰很多！
</span>

### 3.3/6题：

**问题1：** 没写清楚是否用反证法.

如果不写反证法假设$f(y)>0$对任意$y\in[a,b]$恒成立，那么构造数列的时候, 
用$f(y_n)\le \dfrac{f(y_0)}{2^n}$推不出$\lim\limits_{n\to\infty}f(y_n)=0$. 

**问题2：** 有同学直接对下式让$n\to\infty$. 

$$f(x_1) \ge 2^{n-1}f(x_n)$$

然后声称右边趋于无穷. 正确的做法是根据反证法的假设以及连续性的条件推出$f(x)$有正的下界, 
才能让$n\to\infty$. 



## 作业之后的思考题:（此部分思考题为助教友情提供，与上课无关，感兴趣可以做，不感兴趣可以不做）

**1.** 设函数$f$定义在区间$(a,+\infty)$上, 并在每个有穷区间$(a,b)$上有界. 又设

$$\lim\limits_{x\to+\infty}\dfrac{f(x+1)-f(x)}{x^p}=c,$$

其中$p$为正的常数. 证明:

$$\lim\limits_{x\to+\infty}\dfrac{f(x)}{x^{p+1}}=\dfrac{c}{p+1}.$$

{: .note }
> 上次有位同学问了我推论3.3.8怎么理解. 然后后来我想了想，这个问题很适合用来修改一下然后练习举反例的能力. 

**2.** 在梅加强《数学分析》书上的推论3.3.8证明了：

> **推论3.3.8** 设$f$是定义在区间$I$中的单调函数，则$f$的间断点全体组成至多可数集. 

我们来修改一下条件，看看结论还对不对. 如果对请给出证明，如果不对请举出反例：

(1)去掉“单调函数”的条件;

(2)把$f$的条件修改为“$f$在区间$I$中每一点都存在左极限和右极限”.
{% endraw %}
