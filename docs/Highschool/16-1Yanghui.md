---
layout: default
title: 16.1 杨辉三角
parent: 高中数学
nav_order: 1601
has_children: false
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


{% raw %}

本公众号的“教材导读”系列是为了让同学或老师意识到教材后面“阅读与思考”部分和“拓广探索”习题部分的重要性, 并提供学习上的引导。通过一系列的简单设问带领同学们去提出问题、解决问题。最后，“课后练习”由高考题、优秀模拟题或者Fiddie原创题组成，供同学们训练。除此之外还有“自主探究”部分，供同学们自己摸索新定义的解答.

**说明：** 
- 所有的“问题”均不提供答案，希望由同学们自行去发现这些“问题”的答案。
- 如果老师们想在上课使用该讲义，可带着学生一起学习，但不要直接把答案告诉学生。
- 注意，“自主探究”部分仍应交给学生自行探索；如果学生在“自主探究”过程中卡住了，老师可以向学生提示该怎么走。
- 如果需要打印本文，可用Chrome或Edge浏览器打开，然后按Ctrl+P打印，另存为PDF文件，再去打印。
- 用手机阅读的时候有些公式可能太长而一行放不下，可左右拖拽公式. 

> 温馨提示：如果老师们在上课过程中使用了该讲义，欢迎向Fiddie分享使用心得，提出您的改进建议！谢谢！我会结合使用者的反馈不断调整更新这份讲义。

# 第十六章 计数原理

# 16.1 杨辉三角

本次导读的内容包括: 
- 杨辉三角的历史
- 杨辉三角与二项式系数的性质
- 李善兰的求和公式
- 自主探究：组合恒等式的证明

本节目标是让同学们学会“大胆猜想、严谨求证”的思想. 首先, 根据“杨辉三角”, 大胆猜测可能成立的一些命题, 
然后再去给出这些命题的严谨证明. 

> 教材: (均采用按照《普通高中数学课程标准(2017年版)》编的教材). 
>
> 人教A版选择性必修第三册第六章6.3.2小节(32-33页、39-41页)   
> 人教B版选择性必修第二册第三章3.3节(31-32页)     
> 苏教版选择性必修第二册习题7.4“探究·扩展”第14题. (81页)    
> 沪教版选择性必修第二册6.5节(35-36页)     
> 北师大版选择性必修第一册第五章“阅读材料”(173-174页)    

## 一、杨辉三角的历史

从《九章算术》的开平方术、开立方数和刘徽注中可知, 古代数学家已经知道

$$\begin{aligned}
(1+x)^2&=1+2x+x^2, \\
(1+x)^3&=1+3x+3x^2+x^3
\end{aligned}$$

两式的代数意义. 

杨辉三角大约于1050年由贾宪(1010-1070)进行高次开方运算时提出, 故也有“贾宪三角”之称. 
贾宪把上述公式扩充到$(1+x)^6$的展开式, 并指出各项系数所遵循的规律.
我国南宋数学家杨辉(1238-1298)在1261年所著的《详解九章算法》一书中记载了“贾宪三角”, 
因其影响更广而被称为“杨辉三角”(如图1).

<div align = center>
<img src="/pics/highschool/yanghui1.jpg" width = "400"/>

<br/>

图1: 《详解九章算法》中记载的杨辉三角
</div>



<div align = center>
<img src="/pics/highschool/yanghui2.png" width = "240"/>

<br/>

图2: 杨辉三角(写成阿拉伯数字)
</div>


图1中杨辉三角下方有五句话. 前两句, “左袤乃积数, 右袤乃隅算”, “袤”字本是“衺”字, 衺是古“邪”字, 通“斜”.
就是说, 左边斜线上的数字(一、一、一……)是各次开方积(常数项)的系数,
右边斜线上的数字(一、一、一……)是各项开方的 “隅算”($x^n$项)的系数.
第三句“中藏者皆廉”是说图中各横行中的“二”, “三、三”, 
“四、六、四”等分别是二次方、三次方、四次方时除“积”“隅”以外各项的系数（“廉”）.
“以廉乘商方”是说用各次廉乘商(一位得数)的相应次方.
“命实而除之”是说从被开方数“实”中减去最后所得的廉与商的乘积．

元朝数学家朱世杰(1249-1314)在1303年的《四元玉鉴》中的“古法七乘方图”也给出了二项式系数(如图3). 

<div align = center>
<img src="/pics/highschool/yanghui3.png" width = "300"/>

<br/>

图3: 古法七乘方图
</div>



在欧洲, 二项式系数是由吉尔松尼德(Levi ben Gershon, 1288-1344)在14世纪初用乘法公式计算出来的.
法国数学家帕斯卡(Blaise Pascal, 1623-1662)在《论算术三角形》(Traité du triangle arithmétique)中,
介绍了由二项式系数所构成的三角形, 并以此解决一些与概率有关的问题, 影响广泛, 所以这个表也被称为帕斯卡三角形(如图4).
这也表明, 我国发现杨辉三角要比欧洲早五百年左右．

<div align = center>
<img src="/pics/highschool/yanghui4.png" width = "360"/>

<br/>

图4: 帕斯卡三角形
</div>

杨辉三角是中国古代数学的杰出研究成果之一, 它把二项式系数图形化, 把组合数内在的一些代数性质直观地从图形中体现出来,
是一种离散型的数与形的结合.

## 二、杨辉三角与二项式系数的关系

杨辉三角数表满足下面的性质: 
- **性质1：** 每一行都是对称的, 且两端的数都是1;
- **性质2：** 每一行的数呈中间大、两边小的特点;
- **性质3：** 从第三行起, 不在两端的任意一个数, 都等于上一行中与这个数相邻的两数之和.

我们根据上面的性质来研究二项式系数, 即组合数$C_n^k$. 

> **问题1：** 对$(1+x)^2, (1+x)^3, (1+x)^4, (1+x)^5$进行二项式展开.

观察$(1+x)^k$每一项的系数, 可以发现, 杨辉三角中第$k+1$行的数字恰好就是$(1+x)^k$的所有系数. 
于是, 我们可以把这个数表改写为如下形式: 

<div align = center>
<img src="/pics/highschool/yanghui5.png" width = "240"/>

<br/>

图5：改写成二项式系数后的杨辉三角
</div>

> **问题2：** 根据性质1, 可以得到组合数的对称性. 写出对应的表达式.
> 
> **问题3：** 根据性质2, 二项式系数$C_n^0,C_n^1,\cdots,C_n^{n-1},C_n^n$
> 满足一个不等式关系, 写出这个不等式关系. (提示: 讨论$n$的奇偶性. ) 
> 
> **问题4：** 根据性质3, 可以写出组合数$C_{n+1}^{k+1}$, 
> $C_{n}^k$, $C_{n}^{k+1}$满足的恒等式. 

我们再来观察一下杨辉三角, 如下图, 把长斜线上的数相加, 你能观察到什么规律吗? 

<div align = center>
<img src="/pics/highschool/yanghui6.png" width = "260"/>

<br/>

图6：含斜线的杨辉三角
</div>


对比二项式系数, 可以发现:

$$\begin{aligned}
&C_1^1+C_2^1+C_3^1+\cdots+C_n^1=C_{n+1}^2, \\
&C_2^2+C_3^2+C_4^2+\cdots+C_n^2=C_{n+1}^3, \\
\end{aligned}$$

> **问题5：** 把上面的公式的$1$和$2$推广到一般的$r$. 当$n \ge r$时, 能得出什么样的恒等式? 

## 三、性质的证明

有了观察之后, 我们要给出严格的证明. 回顾组合数的定义: 当$k\in\{0,1,\cdots,n\}$时, 

$$C_n^k = \dfrac{n!}{k!(n-k)!}.$$

{: .theorem-title}
> 定理1
> 
> $C_n^k = C_n^{n-k}.$

**证明:** 因为

$$\begin{aligned}
C_n^k &= \dfrac{n!}{k!(n-k)!}, \\
C_n^{n-k} &= \dfrac{n!}{(n-k)!(n-(n-k))!} = \dfrac{n!}{(n-k)!k!},
\end{aligned}$$

所以$C_n^k = C_n^{n-k}.$ 
证明完毕. $\square$

接下来探究一下“问题3”涉及到的单调性的证明. 从函数角度看, $C_n^r$可以看成以$r$为自变量的函数$f(r)$, 
其定义域是$\{0,1,\cdots,n\}$. 为了证明相邻两项的单调性, 即比较$f(r-1)$与$f(r)$的大小, 其中$r$是正整数.
这等价于比较$\dfrac{f(r)}{f(r-1)}$与$1$的大小. 

> **问题6：** 用组合数的定义, 证明: 当$r\in\{1,2,\cdots,n\}$时, 
> $\dfrac{f(r)}{f(r-1)} = \dfrac{n-r+1}{r}.$

我们可以发现, $\dfrac{f(r)}{f(r-1)} < 1$当且仅当$\dfrac{n-r+1}{r} < 1$, 当且仅当$r > \dfrac{n+1}{2}$. 
同理, 

> **问题7：** $\dfrac{f(r)}{f(r-1)} > 1$当且仅当 __________________________ .
> $n,r$满足什么条件的时候, $\dfrac{n-r+1}{r}$可以取到$1$? 

有了上述准备, 我们可以把单调性的结论证明出来了. 

> **问题8：** 证明定理2. 

{: .theorem-title}
> 定理2
> 
> 当$n$是偶数时, $f(r)$在$r\le \dfrac{n}{2}$时单调递增, 在$r\ge \dfrac{n}{2}$时单调递减.
> 当$n$是奇数时, $f(r)$在$r\le \dfrac{n-1}{2}$时单调递增, 在$r = \dfrac{n-1}{2}$与$r=\dfrac{n+1}{2}$时取到最大值, 
> 在$r\ge \dfrac{n+1}{2}$时单调递减. 

接下来我们证明问题4的结论. 这里编者要求同学们学会“读懂一个证明”. 读懂一个证明的关键在于知道每一步的理由是什么. 

{: .theorem-title}
> 定理3
> 
> 当自然数$k$满足$k\le n$时, 
> $C_{n+1}^{k+1} = C_{n}^k + C_{n}^{k+1}.$

**证明：** 因为

$$\begin{aligned}
C_{n}^{k} + C_n^{k+1}
&=\dfrac{n!}{k!(n-k)!} + \dfrac{n!}{(k+1)!(n-k-1)!} \\
&=\dfrac{n!}{k!(n-k)!} + \dfrac{n!}{k!(n-k)!}\cdot \dfrac{n-k}{k+1} \\
&=\dfrac{n!}{k!(n-k)!}\left(1+\dfrac{n-k}{k+1}\right) \\
&=\dfrac{n!}{k!(n-k)!}\cdot\dfrac{n+1}{k+1} \\
&=\dfrac{(n+1)!}{(k+1)!(n-k)!} \\
&=C_{n+1}^{k+1}.
\end{aligned}$$

因此, 欲证结论成立. $\square$

> **问题9：** 请解释上面每个等号的理由. 
> 
> 第一个等号是因为 ___________________________________________ .      
> 
> 第二个等号是因为在问题6的结论中让$r =$ ______________________ .            
> 
> 第三、第四个等号是因为合并同类项与化简.   
> 
> 第五个等号是因为 ___________________________________________ .     
>  
> 第六个等号是因为 ___________________________________________ . 

{: note}
> 接下来的内容需要用到数列知识. 

接下来给出给出问题5的证明. 问题5的答案是

$$C_r^r+C_{r+1}^r+C_{r+2}^r+\cdots+C_n^r = C_{n+1}^{r+1}.$$

这里要求同学们学过“数列求和”的知识, 没学过数列可以跳过.

首先, 固定正整数$r$, 根据定理3(把$k$换成$r$), 我们有

$$C_{n+1}^{r+1} = C_{n}^r + C_{n}^{r+1}.$$

改写为

$$C_{n+1}^{r+1} - C_{n}^{r+1} = C_{n}^r.$$

注意$r$是固定的, 我们定义数列$\{a_n\}$为$a_n = C_n^{r+1}$. 于是上式可以改写为

$$a_{n+1} - a_n = C_n^r.$$

接下来利用裂项相消法求和, 把上式$n$取为$r,r+1,\cdots,n$然后再叠加. 

> **问题10：** 利用裂项相消法求和, 能得出什么式子? 
> 
> **问题11：** 请整理问题11中的式子, 最终我们完成定理4的证明.  

{: .theorem-title}
> 定理4
> 
> 当正整数$r\le n$时, 有
>
> $$C_r^r+C_{r+1}^r+C_{r+2}^r+\cdots+C_n^r = C_{n+1}^{r+1}.$$

## 四、李善兰的求和公式


清代数学家李善兰(1811-1882)于1859年在《垛积比类》中得到了“高阶等差数列”$\{n^p\}$的求和公式($p$是正整数). 

<div align = center>
<img src="/pics/highschool/duojibilei.png" width = "350"/>

<br/>

图7：《垛积比类》
</div>



他的思路如下: 首先他发现了

$$\begin{aligned}
n^2&=C_n^2 + C_{n+1}^2 \\
n^3&=C_{n}^3+4C_{n+1}^3 + C_{n+2}^3 \\
n^4&=C_{n}^3+11C_{n+1}^4 + 11C_{n+2}^4 + C_{n+3}^4 \\
n^5&=C_{n}^5+26C_{n+1}^5 + 66C_{n+2}^5 + 26C_{n+3}^5 + C_{n+4}^5
\end{aligned}$$

(如果$C_n^k$中$k > n$, 约定$C_n^k=0$. )

> **问题12：** 基于上面的几条式子与定理4, 推导出$\{n^p\}(p=1,2,3,4,5)$的前$n$项和公式.

一般地, $n^p$可写成

$$\begin{aligned}
n^p &= A_{p,0}C_{n}^p + A_{p,1}C_{n+1}^p + \cdots + A_{p,p-1}C_{n+p-1}^p \\
&= \sum\limits_{k=0}^{p-1} A_{p,k}C_{n+k}^p.
\end{aligned}$$

其中, $A_{i,j}$叫做**欧拉数(Eulerian number)**, 而这个等式又称作**Worpitzky恒等式**(由德国数学家Julius Worpitzky在1883年发现). 

欧拉数满足下面的递推关系式:

$$A_{p+1,k} = kA_{p,k} + (p+2-k)A_{p,k-1}.$$

我们可以把$A_{i,j}$写成下面的数阵形式, 叫做**欧拉三角**: 

<div align = center>
<img src="/pics/highschool/EulerianNumbers.png" width = "300"/>

<br/>

图8：欧拉三角
</div>



于是, 数列$\{n^p\}$($p$是任意正整数)都可以通过欧拉三角中的系数与定理4的式子得出. 

**注：** 欧拉数的背景并不是“高阶等差数列”. 事实上, 
欧拉(Leonhard Euler, 1707-1783)在1755年研究了如下问题: 

{: .problem-title}
> 问题
>
> 把$n$个正整数$1,2,\cdots,n$重新排成$a_1,a_2,\cdots,a_n$,
> 恰有$k$个位置上的数在重排后大于该位置前面的数(即共有$k$个正整数$m$使得$a_m > a_{m-1}$)的情况有多少种? 

经过欧拉的研究, 上述问题的情况种数恰好就是$A_{n,k}$个. 显然$A_{n,n}=0$. 


<div align = center>
<img src="/pics/highschool/Euler.jpg" width = "200"/>

<br/>

图9：欧拉
</div>


把$1,2,\cdots,n$重新排成$a_1,a_2,\cdots,a_n$的方式共$n!$种(作全排列), 利用分类加法原理, 可得

$$n! = \sum\limits_{k=0}^n A_{n,k}.$$

因此, 我们得到了如下结论: 

> **问题13：** 欧拉三角的第$n$行各数之和为 ____________________________ . 

“高阶等差数列”问题和研究$n$个正整数的重排的问题看似毫不相关, 然而却可以通过Worpitzky恒等式建立联系,
这就体现了数学的神奇之处.

## 课后习题

请把课后习题当做解答题来完成, 不仅要得到答案(这只是“观察猜想”的步骤), 也要给出合理的解释. 3~5题有提示，如果想不出来可以先看看提示. 

**1.【2008上海, 12】**       
组合数$C_n^r(n>r\ge 1, n,r\in\mathbf{Z})$恒等于 
- A. $\dfrac{r+1}{n+1}C_{n-1}^{r-1}$
- B. $(n+1)(r+1)C_{n-1}^{r-1}$
- C. $nrC_{n-1}^{r-1}$
- D. $\dfrac{n}{r}C_{n-1}^{r-1}$

**2.【2017届湖北黄石9月调研(改编)】**       
将三项式$(x^2+x+1)^n$展开, 当$n=0,1,2,3,\cdots$时, 得到下面的展开式. 

$$\begin{aligned}
(x^2+x+1)^0&=1 \\
(x^2+x+1)^1&=x^2+x+1 \\
(x^2+x+1)^2&=x^4+2x^3+3x^2+2x+1 \\
(x^2+x+1)^3&=x^6+3x^5+6x^4+7x^3+6x^2+3x+1 \\
(x^2+x+1)^4&=x^8+4x^7+10x^6+16x^5+19x^4+16x^3+10x^2+4x+1 \\
\end{aligned}$$

观察多项式系数之间的关系, 可以仿照杨辉三角构造如图所示的“广义杨辉三角”(如下图). 

<div align = center>
<img src="/pics/highschool/yanghui8.png" width = "350"/>
</div>

其构造方式为: 第0行为1, 以下各行每个数是它头上与左右两肩上3个数之和(不足3数的, 缺少的数计为$0$),
第$k$行共有$2k+1$个数. 则对于任意正整数$n$, “广义杨辉三角”中第$n$行的各数之和为 ____________________________ ; 
在$(1+2x)(x^2+x+1)^n$的展开式中, $x^{2n-1}$项的系数为 ____________________________ . 

**3.【2007湖南, 15】**      
将杨辉三角中的奇数换成1, 偶数换成0, 得到如图所示的0-1三角数表.
从上往下数, 第1次全行的数都为1的是第1行, 第2次全行都为1的数都为1的是第3行, $\cdots$,
第$n$次全行的数都为1的是第 __________________________ 行; 第61行中1的个数是 ____________________________.

<div align = center>
<img src="/pics/highschool/2007hunan15.png" width = "250"/>
</div>

**4.【2006湖北, 15改编】**      
将杨辉三角中的每一个数$C_n^r$都换成$\dfrac{1}{(n+1)C_n^r}$,
就得到一个如下图所示的分数三角形, 称为莱布尼茨三角形.
从莱布尼茨三角形可看出$\dfrac{1}{(n+1)C_n^r}+\dfrac{1}{(n+1)C_n^x}=\dfrac{1}{nC_{n-1}^r}$,
其中$x=$ __________________________ .
令$a_n=\dfrac{1}{3}+\dfrac{1}{12}+\dfrac{1}{30}+\dfrac{1}{60}+\cdots+\dfrac{1}{nC_{n-1}^2}+\dfrac{1}{(n+1)C_n^2}$,
则数列$\{a_n\}$的前$100$项和为 _________________________ (用最简分数表示). 

<div align = center>
<img src="/pics/highschool/2006hubei15.png" width = "340"/>
</div>


**5.【2016广州一模(改编)】**      
以下数表的构造思路源于我国南宋数学家杨辉所著的《详解九章算术》一书中的“杨辉三角形”．

<div align = center>
<img src="/pics/highschool/2016guangzhou.png" width = "470"/>
</div>

该表由若干行数字组成, 从第二行起, 每一行中的数字均等于其“肩上”两数之和. 
若第一行有$n(n\in\mathbf{N}^*)$个数, 则第$k(1\le k\le n)$行是公差为 __________________________ 的等差数列. 
表中最后一行仅有一个数, 这个数为 ____________________________ . (用含$n$的表达式表示.)


## 自主探究：证明组合恒等式

我们已经证明了如下恒等式, 其中$n$是正整数, $k,r$是自然数, $k\le n$, $r\le n$. 

$$\begin{aligned}
&C_n^0+C_n^1+\cdots+C_n^n = 2^n \\
\text{定理3：}&C_{n+1}^{k+1} = C_{n}^k + C_{n}^{k+1} \\
\text{定理4：}&\sum\limits_{k=0}^{n-r} C_{r+k}^r = C_{n+1}^{r+1}
\end{aligned}$$

这些恒等式都属于**组合恒等式**. 我们来探索更多组合恒等式的证明方法. 

在证明定理4的时候, 我们把一个求和的式子利用定理3的式子写成了两式相减的形式, 然后把若干个式子叠加即可得到一个组合恒等式. 

> **问题1：** 证明: $(m+1+k)C_{m+k}^m = (m+1)C_{m+k+1}^{m+1}$.
> 
> **问题2：** 证明: 当正整数$m,n$满足$m\le n$时, 有
> 
> $$\sum\limits_{k=0}^{n-m} (m+1+k)C_{m+k}^m = (m+1)C_{n+2}^{m+2}.$$

除了裂项相消的思想之外, 我们也可以用导数的工具. 如果一个等式$f(x)=g(x)$对任意$x\in\mathbf{R}$都成立,
那么其导函数也有恒等关系: $f'(x)=g'(x)$对任意$x\in\mathbf{R}$都成立. 

例如, 在等式$\cos 2x=2\cos^2x-1(x\in\mathbf{R})$的两边对$x$求导$(\cos 2x)'=(2\cos^2x-1)'$,
由求导法则得$(-\sin 2x)\cdot 2=4\cos x\cdot(-\sin x)$, 化简后得到等式$\sin 2x=2\sin x\cos x$.

直接从下面的恒等式两边求导:

$$(1+x)^n=C_n^0+C_n^1x+\cdots+C_n^nx^n$$

可以得到一个新的恒等式. 

> **问题3：** 证明: 当$n\ge 2$时, $n\Big[(1+x)^{n-1}-1\Big]=\sum\limits_{k=2}^nkC_n^kx^{k-1}.$

把上述$x$取为特定值, 可以得到许多组合恒等式. 在问题4至问题6中, 设正整数$n\ge 3$. 

> **问题4：** 证明: $\sum\limits_{k=1}^n(-1)^kC_n^k=0$;     
> 
> **问题5：** 证明: $\sum\limits_{k=1}^n(-1)^kk^2C_n^k=0$;     
> 
> **问题6：** 证明: $\sum\limits_{k=0}^{n}\dfrac{1}{k+1}C_n^k=\dfrac{2^{n+1}-1}{n+1}.$

组合恒等式还可用于在概率统计中数学期望的估计. 

已知一个口袋有$m$个白球, $n$个黑球($m,n\in\mathbf{N}^*$, $n\ge 2$),
这些球除颜色外全部相同. 现将口袋中的球随机的逐个取出,
并放入如图所示的编号为$1$,$2$,$3$,$\cdots$,$m+n$的抽屉内,
其中第$k$次取球放入编号为$k$的抽屉($k=1,2,3,\cdots,m+n$).

<div align = center>
<img src="/pics/highschool/2017jiangsu23.png" width = "200"/>
</div>

随机变量$X$表示最后一个取出的黑球所在抽屉编号的倒数, $E(X)$是$X$的数学期望. 
接下来我们要估计$E(X)$的值. 

> **问题7：** 写出$X$的分布列与$E(X)$的表达式(用$m,n$表示). 
> 
> **问题8：** 通过$\dfrac{k-1}{k} < 1$, 说明
> 
> $$E(X) < \dfrac{1}{C_{m+n}^n}\sum\limits_{k=n}^{m+n} \dfrac{(k-2)!}{(n-1)!(k-n)!}.$$
> 
> **问题9：** 仿照定理4的裂项相消过程, 利用定理3的恒等式对问题8的右边进行求和, 从而证明
> 
> $$E(X) < \dfrac{n}{(m+n)(n-1)}.$$

还有一种组合恒等式的证明方法是“算两次”的方法. 
将一个量用两种方法分别算一次,
由结果相同得到等式, 这是一种非常有用的思想方法, 叫作“算两次”.
对此, 我们并不陌生, 如列方程时就要从不同的侧面列出表示同一个量的代数式, 
几何中常用的等积法也是“算两次”的典范. 再如, 
我们还可以用这种方法, 结合二项式定理得到很多组合恒等式, 如由等式

$$(1+x)^{2n}=(1+x)^n(1+x)^n$$

可知, 左边$x^n$的系数为$C_{2n}^n$, 而右边等于

$$\begin{aligned}
&\qquad (1+x)^n(1+x)^n \\
&=(C_n^0+C_n^1x+\cdots+C_n^nx^n)
(C_n^0+C_n^1x+\cdots+C_n^nx^n)
\end{aligned}$$

其中, $x^n$的系数等于

$$\begin{aligned}
&\qquad C_n^0C_n^n+C_n^1C_n^{n-1}+C_n^2C_n^{n-2}
+\cdots+C_n^nC_n^0 \\
&=(C_n^0)^2+(C_n^1)^2+(C_n^2)^2+\cdots+(C_n^n)^2.
\end{aligned}$$

由$(1+x)^{2n}=(1+x)^n(1+x)^n$恒成立, 可得

$$(C_n^0)^2+(C_n^1)^2+(C_n^2)^2+\cdots+(C_n^n)^2=C_{2n}^n,$$

或者写成

$$\boxed{\sum\limits_{k=0}^n(C_n^k)^2 = C_{2n}^n}.$$

我国元末明初时期数学家朱世杰(约1260-约1320)在1303年发现了下面的恒等式, 
而1772年范德蒙(Alexandre-Théophile Vandermonde, 1735-1796)也发现了这个恒等式, 
故下面的恒等式也称朱世杰-范德蒙恒等式(Chu-Vandermonde Identity): 
当$n,p,q$是正整数, 且$p\ge n, q\ge n$时, 有

$$\sum\limits_{k=0}^nC_p^kC_q^{n-k} = C_{p+q}^{n}.$$

> **问题10：** 利用“算两次”的思想, 证明朱世杰-范德蒙行列式.

清代数学家李善兰于1859年在《垛积比类》一书提出了下面的恒等式: 当$n,p,q$是正整数, 且$p\ge n, q\ge n$时, 有

$$\sum\limits_{j=0}^nC_p^jC_q^jC_{p+q+n-j}^{n-j} = C_{p+n}^nC_{q+n}^n.$$

> **问题11：** 证明: 当正整数$n,k,l$满足$n\ge k\ge l$时, 有
> 
> $$C_n^kC_k^l = C_n^l C_{n-l}^{k-l}.$$
> 
> **问题12：** 利用问题11中的式子与朱世杰-范德蒙恒等式, 证明李善兰恒等式.

## 备注与提示

### 课后习题

**3.** (1)把这个杨辉三角的第7行写出来, 猜想结论. (2)第63行全为1, 向前推两行可得第61行中1的个数. 

**4.** (1)为了求$x$, 仿照杨辉三角中“每一项是前一行相邻两项之和”的方式, 来找出莱布尼茨三角满足的恒等式. 
莱布尼茨三角形满足每一项都是后一行相邻两项之和.
(2)为了求$a_n$, 把前面的恒等式变成可以裂项相消的形式. 

**5.** 观察每一行第一个数满足什么样的关系式. 

### 自主探究

问题1提示：仿照定理1证明过程的处理方法.

问题7提示: $E(X) = \sum\limits_{k=n}^{m+n} \dfrac{1}{k}\dfrac{C_{k-1}^{n-1}}{C_{m+n}^n}.$

问题10提示: 考虑$(1+x)^{p+q}$与$(1+x)^p(1+x)^q$, 比较两种写法的$x^n$项的系数. 

问题11提示：仿照定理1证明过程的处理方法.

**注：** 自主探究的问题的来源如下: 

问题2出自2016年江苏高考23题: 

> **6.【2016江苏, 23】**    
> (1) 求$7C_6^3-4C_7^4$的值.     
> 
> (2) 设$m,n\in\mathbb{N}^*$, $n\ge m$, 求证:      
> $(m+1)C_m^m+(m+2)C_{m+1}^m+(m+3)C_{m+2}^m
> +\cdots+nC_{n-1}^m+(n+1)C_n^m=(m+1)C_{n+2}^{m+2}.$

问题3-6出自2008年江苏高考23题:

> **7.【2008江苏, 23】** 请先阅读: 在等式$\cos 2x=2\cos^2x-1(x\in\mathbb{R})$的两边对$x$求导$(\cos 2x)'=(2\cos^2x-1)'$,
由求导法则得$(-\sin 2x)\cdot 2=4\cos x\cdot(-\sin x)$, 化简后得到等式$\sin 2x=2\sin x\cos x$.
> 
> (1) 利用上述想法(或者其他方法), 试由等式
> 
> $$(1+x)^n=C_n^0+C_n^1x+C_n^2x^2+\cdots+
C_n^{n-1}x^{n-1}+C_n^nx^n(x\in\mathbb{R}, \text{整数}n\ge 2)$$
> 
> 证明: $n\Big[(1+x)^{n-1}-1\Big]=\sum\limits_{k=2}^nkC_n^kx^{k-1}.$
> 
> (2) 对于整数$n\ge 3$, 求证:     
> (i)$\sum\limits_{k=1}^n(-1)^kC_n^k=0$;     
> (ii)$\sum\limits_{k=1}^n(-1)^kk^2C_n^k=0$;     
> (iii)$\sum\limits_{k=0}^{n}\dfrac{1}{k+1}C_n^k=\dfrac{2^{n+1}-1}{n+1}.$

问题7-9出自2017年江苏高考23题:

> **8.【2017江苏, 23】** 已知一个口袋有$m$个白球, $n$个黑球($m,n\in\mathbb{N}^*$, $n\ge 2$),
> 这些球除颜色外全部相同. 现将口袋中的球随机的逐个取出,
> 并放入如图所示的编号为$1,2,3,\cdots,m+n$的抽屉内,
> 其中第$k$次取球放入编号为$k$的抽屉($k=1,2,3,\cdots,m+n$).
> 
> 
> <div align = center>
> <img src="/pics/highschool/2017jiangsu23.png" width = "200"/>
> </div>
> 
> 
> (1)试求编号为2的抽屉内放的是黑球的概率$p$;
> 
> (2)随机变量$X$表示最后一个取出的黑球所在抽屉编号的倒数, $E(X)$是$X$的数学期望, 证明: $E(X) < \dfrac{n}{(m+n)(n-1)}$.

## 参考答案

**1.** D. 
提示: $C_{n-1}^{r-1}=\dfrac{(n-1)!}{(r-1)!(n-r)!}$, 而

$$C_n^r = \dfrac{n!}{r!(n-r)!} = \dfrac{n}{r}\cdot \dfrac{(n-1)!}{(r-1)!(n-r)!}=\dfrac{n}{r}C_{n-1}^{r-1}.$$


&nbsp; 

**2.** $3^n$; $n^2+2n$. 

解: (1)为了求第$n$行的各数之和, 注意第$n$行各个数是$(x^2+x+1)^n$每项的系数, 故只需让$x=1$即可得各数之和是$3^n$.      
(2)“广义杨辉三角”的第$n$行共$2n+1$个数, 
第二个空的答案是$(x^2+x+1)^n$展开式中的$x^{2n-2}$项的系数与$x^{2n-1}$项系数的两倍之和, 
即“广义杨辉三角”的从左往右数第2个数与第3个数的两倍之和. 
经过观察可发现, 第$n$行的第2个数和第3个数分别是$n$和$\dfrac{n(n+1)}{2}$, 
故所求系数是$n+2\cdot \dfrac{n(n+1)}{2} = n^2+2n.$

> 思考: 如何证明第$n$行的第2个数和第3个数分别是$n$和$\dfrac{n(n+1)}{2}$？
> 你能否给出“广义杨辉三角”中每个数(你可以称之为“三项式系数”)的通项公式? 

&nbsp; 

**3.** $2^n-1$; 32. 

提示: 
我们可以定义一种新的运算$\oplus$如下: $0\oplus 0=0$, $0\oplus 1=1$, $1\oplus 0=1$, $1\oplus 1=0$.
这样我们在定义杨辉三角时, 第$n+1$行由两端为1、中间的数由第$n$行的相邻两数按$\oplus$相加而成.  
我们先把这个杨辉三角写到第7行, 可以发现第7行也是全是1的, 故第3次出现全是1的是第7行.
猜想: 第$n$次出现全是1的是第$2^n-1$行. 由猜想, $n=6$时, 第6次出现全是1的是第63行, 
于是可向前推出第61行如下: 

<div align = center>
<img src="/pics/highschool/2007hunan15k.png" width = "600"/>
</div>


第61行是“$1,1,0,0$”周期出现, 且最后两个数是“$1,1$”. 因此一共有$32$个1和$30$个0. 


&nbsp; 

**4.** $r+1$; $\dfrac{4950}{101}$. 

提示: (1)通过观察, 每个数是其下方两个数之和. 因此$x=r+1$. 也可以证明如下: 注意

$$\begin{aligned}
C_n^{r+1}& =\dfrac{n!}{(r+1)!(n-r-1)!} \\
&=\dfrac{n-r}{r+1}\cdot\dfrac{n!}{r!(n-r)!} \\
&=\dfrac{n-r}{r+1}C_{n}^{r}.
\end{aligned}$$

因此

$$\begin{aligned}
&\qquad\dfrac{1}{(n+1)C_n^r}+\dfrac{1}{(n+1)C_n^{r+1}} \\
&=\dfrac{1}{(n+1)C_n^r}+\dfrac{1}{(n+1)C_n^{r}}\cdot\dfrac{r+1}{n-r}  \\
&=\dfrac{1}{(n+1)C_n^r}\cdot\left(1+\dfrac{r+1}{n-r}\right) \\ 
&= \dfrac{1}{(n+1)C_n^r}\cdot \dfrac{n+1}{n-r} = \dfrac{1}{(n-r)C_n^r}. 
\end{aligned}$$

注意, $C_n^r=\dfrac{n!}{r!(n-r)!}=\dfrac{n}{n-r}\cdot\dfrac{(n-1)!}{r!(n-1-r)!}=\dfrac{n}{n-r}C_{n}^{r-1}$,
因此$(n-r)C_n^r=nC_{n-1}^{r}$, 
从而$\dfrac{1}{(n+1)C_n^r}+\dfrac{1}{(n+1)C_n^{r+1}}=\dfrac{1}{nC_{n-1}^{r}}$. 

(2)由(1), 令$r=1$可得$\dfrac{1}{(n+1)C_n^2}=\dfrac{1}{nC_{n-1}^1}-\dfrac{1}{(n+1)C_n^1}$. 
记$b_n=\dfrac{1}{nC_{n-1}^1}(n\ge 2)$, 于是$\dfrac{1}{(n+1)C_n^2}=b_n-b_{n+1}$, 因此
 
$$\begin{aligned}
a_n&=\dfrac{1}{3C_2^2}+\dfrac{1}{4C_3^2}+\cdots+\dfrac{1}{(n+1)C_n^{2}} \\
&=(b_2-b_3)+(b_3-b_4)+\cdots+(b_n-b_{n+1}) \\
&=b_2-b_{n+1}=\dfrac{1}{2}-b_{n+1} = \dfrac{1}{2} - \dfrac{1}{n(n+1)}.
\end{aligned}$$

所以$\{a_n\}$的前100项和为

$$100\times\dfrac{1}{2} - \left(1-\dfrac{1}{101}\right) = 49+\dfrac{1}{101} = \dfrac{4950}{101}.$$

也可以这样理解: 第二问是求莱布尼茨三角形中从第三行起每一行的第三项之和, 
根据第一问, 只需在原式基础上增加一项$\dfrac{1}{(n+1)C_n^1}$, 
则由每一行中的任一数都等于其“脚下”两数之和, 当$n\to\infty$时, 结合给出的数表可逐次向上求和为$\dfrac{1}{2}$. 

&nbsp; 

**5.** $2^{k-1}$; $(n+1)\cdot 2^{n-2}$. 

提示: 【方法一】归纳推理. 当第一行3个数时，最后一行仅一个数为$8=2^{3-2}\times (3+1)$.     
当第一行4个数时，最后一行仅一个数为$20=2^{4-2}\times(4+1)$.     
当第一行5个数时，最后一行仅一个数为$48=2^{5-2}\times(5+1)$.     
当第一行6个数时，最后一行仅一个数为$112=2^{6-2}\times(6+1)$.     
归纳推理，得：     
当第一行$n$个数时，最后一行仅一个数为$2^{n-2}\times(n+1)$. 

【方法二】严格证明. 假设第一行有$n$个数时, 最后一行仅有的一个数是$a_n$. 
则此时第$k$行的第一个数为$a_k$(首项$a_1=1$), 并且第$k$行($1\le k\le n$)的第二个数为$a_k+2^{k-1}$. 
所以根据这个数表的构造, 可知$a_{k+1}$是其肩上两个数之和, 即

$$a_{k+1} = a_k + (a_k+2^{k-1}) = 2a_k + 2^{k-1}.$$

于是转化为了我们熟悉的数列求和. 上式等号两边同除以$2^{k+1}$, 可得

$$\dfrac{a_{k+1}}{2^{k+1}} = \dfrac{a_k}{2^k} + \dfrac{1}{4},$$

因此$\left\lbrace\dfrac{a_n}{2^n}\right\rbrace$是首项为$\dfrac{a_1}{2} = \dfrac{1}{2}$, 公差为$\dfrac{1}{4}$的等差数列.
于是$\dfrac{a_n}{2^n} = \dfrac{1}{4}(n+1)$, 从而

$$a_n = \dfrac{1}{4}(n+1)\cdot 2^n = (n+1)\cdot 2^{n-2}.$$


### 自主探究引用的习题答案

**6.** (1)$7C_6^3-4C_7^4=7\times 20-4\times 35=0$. 

(2)当$n=m$时, 结论显然成立. 当$n>m$时, 注意到

$$\begin{aligned}
(k+1)C_k^m&=\dfrac{(k+1)\cdot k!}{m!(k-m)!} \\
&=(m+1)\dfrac{(k+1)!}{(m+1)![(k+1)-(m+1)]!} \\
&=(m+1)C_{k+1}^{m+1},
\end{aligned}$$

其中$k=m+1,m+2,\cdots,n.$

又因为$C_{k+1}^{m+1}+C_{k+1}^{m+2}=C_{k+2}^{m+2}$, 所以

$$(k+1)C_k^m=(m+1)(C_{k+2}^{m+2}-C_{k+1}^{m+2}), $$

其中$k=m+1,m+2,\cdots,n.$ 因此,
 
$$\begin{aligned}
&\quad (m+1)C_m^m+(m+2)C_{m+1}^m+(m+3)C_{m+2}^m+\cdots+(n+1)C_n^m \\
&=(m+1)C_{m+2}^{m+2}+\Big[(m+1)(C_{m+3}^{m+2}-C_{m+2}^{m+2})+(C_{m+4}^{m+2}-C_{m+3}^{m+2})
+\cdots+(C_{n+2}^{m+2}-C_{n+1}^{m+2})\Big] \\
&=(m+1)C_{n+2}^{m+2}.
\end{aligned}$$

**7.** (1)根据等式$(1+x)^n=C_n^0+C_n^1x+C_n^2x^2+\cdots+C_n^{n-1}x^{n-1}+C_n^nx^n$, 整理可得恒等式

$$(1+x)^n-1-nx = \sum\limits_{k=2}^nC_n^kx^k.$$

对上式两边求导, 可得

$$n(1+x)^{n-1}-n = \sum\limits_{k=2}^nkC_n^kx^{k-1}.$$

因此, $n[(1+x)^{n-1}-1]=\sum\limits_{k=2}^nkC_n^kx^{k-1}$. 

(2)(i)对于整数$n\ge 3$, 在(1)中令$x=-1$, 可得$-n = \sum\limits_{k=2}^nkC_n^k(-1)^{k-1}$, 因此

$$\sum\limits_{k=1}^nkC_n^k(-1)^{k}=-\sum\limits_{k=1}^nkC_n^k(-1)^{k-1}
 = -1\times C_n^1(-1)^{1-1} - \sum\limits_{k=2}^nkC_n^k(-1)^{k-1} = 0.$$

(ii)对(1)中式子两边同乘$x$, 可得恒等式

$$nx(1+x)^{n-1}=\sum\limits_{k=1}^nkC_n^kx^{k}. $$

对上式求导, 可得

$$n(1+x)^{n-1}+n(n-1)x(1+x)^{n-2} = \sum\limits_{k=1}^nk^2C_n^kx^{k-1}.$$

在上式让$x=-1$, 可得$\sum\limits_{k=1}^nk^2C_n^k(-1)^{k-1}=0$, 因此

$$\sum\limits_{k=1}^nk^2C_n^k(-1)^{k}=-\sum\limits_{k=1}^nk^2C_n^k(-1)^{k-1} = 0. $$

(iii)因为

$$\dfrac{1}{k+1}C_n^k=\dfrac{1}{k+1}\cdot\dfrac{n!}{k!(n-k)!} =
\dfrac{1}{n+1}\dfrac{(n+1)!}{(k+1)!(n-k)!} = \dfrac{1}{n+1}C_{n+1}^{k+1},$$ 

所以

$$\sum\limits_{k=0}^n\dfrac{1}{k+1}C_n^k
=\dfrac{1}{n+1}\sum\limits_{k=0}^nC_{n+1}^{k+1}
=\dfrac{1}{n+1}\sum\limits_{l=1}^{n+1}C_{n+1}^l,$$

在$(1+x)^n=C_n^0+C_n^1x+C_n^2x^2+\cdots+C_n^{n-1}x^{n-1}+C_n^nx^n$中, 把$n$换为$n+1$, 取$x=1$, 可得

$$2^{n+1}=C_{n+1}^0+\sum\limits_{l=1}^{n+1}C_{n+1}^l,$$

于是$\sum\limits_{l=1}^{n+1}C_{n+1}^l = 2^{n+1}-1$, 从而

$$\sum\limits_{k=0}^n\dfrac{1}{k+1}C_n^k=
\dfrac{1}{n+1}\sum\limits_{l=1}^{n+1}C_{n+1}^l = \dfrac{2^{n+1}-1}{n+1}.$$

**8.** (1)编号为2的抽屉内放的是黑球的概率$p=\dfrac{C_{m+n-1}^{n-1}}{C_{m+n}^n}=\dfrac{n}{m+n}$.

(2)证明: 随机变量$X$的概率分布为

<div align = center>
<img src="/pics/highschool/2017jiangsu23k.png" width = "550"/>
</div>


随机变量$X$的期望为

$$E(X)=\sum\limits_{k=n}^{m+n}\dfrac{1}{k}\dfrac{C_{k-1}^{n-1}}{C_{m+n}^n}
=\dfrac{1}{C_{m+n}^n}\sum\limits_{k=n}^{m+n}\dfrac{1}{k}\cdot\dfrac{(k-1)!}{(n-1)!(k-n)!} $$

利用恒等式$C_{n+1}^r=C_n^{r-1}+C_n^r$, 可得

$$\begin{aligned}
E(X)& < \dfrac{1}{C_{m+n}^n}\sum\limits_{k=n}^{m+n}\dfrac{(k-2)!}{(n-1)!(k-n)!} \\
&=\dfrac{1}{(n-1)C_{m+n}^n}\sum\limits_{k=n}^{m+n}\dfrac{(k-2)!}{(n-2)!(k-n)!} \\
&=\dfrac{1}{(n-1)C_{m+n}^n}(1+C_{n-1}^{n-2}+C_n^{n-2}+\cdots+C_{m+n-2}^{n-2}) \\
&=\dfrac{1}{(n-1)C_{m+n}^n}(C_{n-1}^{n-1}+C_{n-1}^{n-2}+C_n^{n-2}+\cdots+C_{m+n-2}^{n-2}) \\
&=\dfrac{1}{(n-1)C_{m+n}^n}(C_{n}^{n-1}+C_n^{n-2}+\cdots+C_{m+n-2}^{n-2}) \\
&=\cdots=\dfrac{1}{(n-1)C_{m+n}^n}(C_{m+n-2}^{n-1}+C_{m+n-2}^{n-2}) \\
&=\dfrac{1}{(n-1)C_{m+n}^n}C_{m+n-1}^{n-1} \\
&=\dfrac{n}{(m+n)(n-1)},
\end{aligned}$$

所以$E(X) < \dfrac{n}{(m+n)(n-1)}.$

{% endraw %}