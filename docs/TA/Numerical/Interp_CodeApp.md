---
layout: default
title: 插值：在信息论中的应用
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 56
---

# 插值在信息论中的应用

{: .note}
> 摘自2024年[南京大学计算机系《计算方法》课件](https://tcs.nju.edu.cn/wiki/index.php?title=%E8%AE%A1%E7%AE%97%E6%96%B9%E6%B3%95_Numerical_method_(Spring_2024)).

多项式插值的原理看似简单，但简单的原理也可以有非凡的应用，这里举一个简单的例子．

{: .problem}
> 11个科学家参与了一个高度保密的项目．科学家们希望把档案锁起来，保密的要求是：当且仅当其中6位或者更多的科学家在场的时候，才能打开所有的锁（进而读取档案）．问题：最少需要多少把锁？每个科学家最少需要同时携带多少把钥匙？

组合问题答案：$\binom{11}{5}=462$把锁，每个科学家需要带$\binom{10}{5}=252$把钥匙．

如果有更多的科学家呢？

1979年，Adi Shamir提出了一个全新的解法：用[多项式插值](https://dl.acm.org/doi/10.1145/359168.359176)！具体步骤如下：
- 把密码/密文藏进一个五次多项式$p(x)$里面
- 每个人手握多项式的一个点值$(x_i,p(x_i))$，点值互不相同
- 任意6个人（或更多），就有了6个数据点
- 通过Lagrange插值，即可唯一地还原多项式$p(x)$



{: .remark}
> 实际的算法使用的是有限域而非实数域
> 
> 有限域多项式指的是系数取值为有限域$F$的多项式，即多项式环$F[x]$中的元素．例如，$F$可以取$\mathbb{Z}/q\mathbb{Z}$（其中，$q$是素数）．回顾《近世代数》中学过的构造元素个数是任意素数幂次的域的方法．
> 
> $$p(x)=a_0+a_1x+a_2x^2+\cdots+a_kx^k (\mathrm{mod}\,\,q)$$
> 
> 其中$a_i\in\lbrace 0,1,\cdots,q-1\rbrace$，则$p:\lbrace 0,1,\cdots,q-1\rbrace \to\lbrace 0,1,\cdots,q-1\rbrace$．

{: .remark}
> Ron Rivest, Adi Shamir, Leonard Adleman三人在1977年提出了著名的RSA加密算法，它是互联网通信安全的基石之一．







