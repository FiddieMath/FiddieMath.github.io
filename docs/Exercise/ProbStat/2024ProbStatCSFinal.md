---
layout: default
title: 2024CS-Final
parent: 概率论与数理统计(NJU)
grand_parent: 习题
nav_order: 202401
---

# 概率论与数理统计 2024 Final

任课老师：尹一通，刘景铖

考试时间：2024年6月19日

**说明：** 为方便整理与引用，本文采用的题号与原卷题号不一样．

## 一、多选题和填空题（$4\times 5=20$）

**1．** 设 $A$ 和 $B$ 是概率空间中的事件，以下哪些也是概率空间的事件：

- A．$A\cup B$
- B．$A^c\cap B$
- C．$A\cup B^c$
- D．$A^c\cap B^c$



**2．** 以下哪个是 a.s. 的定义：

- A．$\mathrm{Pr}\Big(\lim\limits_{n\to\infty}X_n=X\Big)=1$
- B．$\lim\limits_{n\to\infty}\mathrm{Pr}\left(X_n=X\right)=1$



**3．** 一个均匀的六面骰子，不停地独立地投掷，直到连续出现两次 6 为止，则投掷次数
的期望为 $\underline{\hspace{2cm}}$ ．



**4．** 一个 𝑛 × 𝑚 的 $0/1$ 网格，每个格子独立地以 $\dfrac{1}{2}$ 的概率取 $1$，以 $\dfrac{1}{2}$ 的概率取 $0$，则每一行和每一列均有偶数个 $1$ 的概率为 $\underline{\hspace{2cm}}$ ．



<div STYLE="page-break-after: always;"></div>


## 二、球与桶模型（20分）

**5．** 有 $𝑛$ 个球，$𝑘$ 个盒子，每个球独立等概率地放入盒子中．

**（1）** 求第一个盒子为空的概率．

**（2）** 求第一个盒子和第二个盒子均为空的概率．

**（3）** 事件“第一个盒子为空”和“第二个盒子为空”是否独立？

**（4）** 设 $𝑘 = 2𝑛 \ln 𝑛$，证明存在一个盒子为空的概率是  $O(\dfrac{1}{n})$ 的．

**（5）** 设 $𝑘 = 𝑛$，证明出现球最多的盒子中的球数多于 $\dfrac{3\ln n}{\ln\ln n}$ 的概率是极小的．


<div STYLE="page-break-after: always;"></div>



## 三、离散随机变量（$2\times 10=20$ 分）

**6．** 设公路上有随机的 $𝑛$ 辆车，它们的车速互不相同，且向同一个方向行驶．如果车速更大的车前面有车速更小的车，则车速更大的车会减速，直到和前面的车速度相同．在经过充分长的时间后，车速相同的车被称为一个“聚类”，求聚类的个数的期望．



**7．** 有 $𝑛$ 个球，依次标号为 $1$ 到 $𝑛$． 按照下面的规则均匀独立地抽球，直到所有球被取出：每次抽球要求本次得到的球是剩下的球中拿出编号最小的球，否则把球放回去．从而，最后拿出的球的编号依次是 $1, 2, \cdots, 𝑛$． 设 $𝑇$ 为抽球的次数，求 $\mathbb{E}(𝑇)$ 和 $\mathrm{Var}(𝑇 )$．



<div STYLE="page-break-after: always;"></div>


## 四、连续随机变量 （$2\times 10=20$ 分）

**8．（1）**设独立的 $X\sim U(0,1)$，$Y\sim U(0,2)$，求

$$
\mathrm{Pr}(\max\{X,Y\}-\min\{X,Y\}\le 1).
$$

**（2）** 设独立的 $Y\sim U(0,1)$，$X$ 定义在 $[0,1]$ 且有概率密度函数 $f_X(x)=2x$，$x\in[0,1]$，求

$$
\mathrm{Pr}(\max\{X,Y\}-\min\{X,Y\}\le 1).
$$

**9．** 两个人打靶．甲打靶时，击中点和靶心的距离服从 $𝑈 (0, 1)$．乙打靶时，击中点在以靶心为圆心的半径为 $1$ 的圆内服从均匀分布．两人公平地选一个人上场打靶．

（1）求击中点到靶心的距离的概率密度函数 $𝑓(𝑥)$．

（2）若已知击中点到靶心的距离为 $\dfrac{1}{2}$，则上场的人是甲的概率是多少．

（3）让已上场的人再开一枪，则此次击中点到靶心的距离的期望是多少．



<div STYLE="page-break-after: always;"></div>


## 五、测度集中和极限定理 （$2\times 10=20$ 分）

**10．（1）** 设 $U$ 是$[0,1]$ 上的均匀分布，求证：$-\log U$ 服从参数为 $1$ 的指数分布．

**（2）** 求

$$
\lim\limits_{n\to\infty}\int_0^1\int_0^1\cdots\int_0^1(x_1x_2\cdots x_n)^{\frac{1}{n}}\mathrm{d}x_1\mathrm{d}x_2\cdots\mathrm{d}x_n.
$$

**（3）** 设 $f$ 是 $[0,1]\to\mathbb{R}$ 上的连续函数，使用大数定律求

$$
\lim\limits_{n\to\infty}\int_0^1\int_0^1\cdots\int_0^1f\left(x_1x_2\cdots x_n)^{\frac{1}{n}}\right)\mathrm{d}x_1\mathrm{d}x_2\cdots\mathrm{d}x_n.
$$

**11．** 回忆对于随机变量 $X$，其矩生成函数为 $M_X(t)=\mathbb{E}[\mathrm{e}^{tX}]$．

（1）若 $\mu=\mathbb{E}[X]$，证明 $M_X(t) \ge \mathrm{e}^{t\mu}$．

（2）设 $X$ 的矩生成函数为 $M_X(t)=\dfrac{\mathrm{e}^t}{1-t^2}$．求 $\mathbb{E}[X]$，并证明对任意 $a>0$，有

$$
\mathrm{Pr}(X\ge a)\le 3\mathrm{e}^{-\frac{a}{2}}.
$$

