---
layout: default
title: (1)椭圆问题的均匀化
parent: 多尺度问题
grand_parent: 讨论班
nav_order: 1
---

发布日期：2022年8月17日

{: .no_toc }

<details open markdown="block">
  <summary>
    目录
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

如果读者们打算详细看这篇文章, 我更建议**直接看英文原版**, 有一些名词其实是**找不到中文翻译**的.

参考书: Weinan E(鄂维南), Principles of Multiscale Modeling-Cambridge University Press (2011).

本文也发在了知乎上，[链接](https://zhuanlan.zhihu.com/p/554826116)

# 0 前言

本来想看Frontiers in Numerical analysis这本书里面的Thomas Y. Hou(侯一钊)写的综述, 但是里面涉及到Einstein记号(我不太熟悉，看着不太顺畅),
所以我们采用鄂维南老师的讲义.

本节首先介绍均匀化方法. 我们先从一个简单的ODE开始考虑, 然后再考虑PDE.

# 1 简单ODE

考虑ODE

$$\begin{aligned}
&\dfrac{\mathrm{d}^2y}{\mathrm{d}t^2}+y+\varepsilon y=0, \\
&y(0)=1, y'(0)=0, \varepsilon \ll 1,
\end{aligned} \tag{1.1}$$

这个ODE可以直接写出真解:

$$y(t)=\cos(\sqrt{1+\varepsilon}t)=\cos\left((1+\dfrac{\varepsilon}{2}+\cdots)t\right).$$

如果在原问题中移除$\varepsilon y$, 那么真解为$y(t)=\cos t$.
在$O(1)$时间尺度上, 这个结果是精确的. 但是在$O(\dfrac{1}{\varepsilon})$的时间尺度上(即更长的时间尺度), 结果与原问题会相差$O(1)$.
(可以理解为: 过了$O(\dfrac{1}{\varepsilon})$时间后, $y(t)$的值与原问题的真解相差$O(1)$. )

为了分析$O(\dfrac{1}{\varepsilon})$时间尺度上的解的表现, 我们用两个时间尺度的展开. 设$\tau=\varepsilon t$是慢时间变量. 假设

$$y(t)\sim y_0(t,\varepsilon t)+\varepsilon y_1(t,\varepsilon t)+\varepsilon^2y_2(t,\varepsilon t).$$

把它代入$(1.1)$, 并令$\tau=\varepsilon t$, 利用链式法则可以求得, 在$\tau=\varepsilon t$的条件下, 有

$$\dfrac{\partial^2y_0}{\partial t^2}+y_0+\varepsilon\left(\dfrac{\partial^2y_1}{\partial t}
+y_1+2\dfrac{\partial^2y_0}{\partial t\partial\tau}+y_0\right)+\cdots\sim 0. \tag{1.2}$$

{: .remark }
> 举个例子,
> 
> $$\begin{aligned}
\dfrac{\mathrm{d}^2}{\mathrm{d}t^2}[y_0(t,\varepsilon t)]
&=\dfrac{\mathrm{d}}{\mathrm{d}t}[\dfrac{\partial}{\partial t}y_0(t,\varepsilon t)
+\varepsilon\dfrac{\partial}{\partial \tau}y_0(t,\varepsilon t)] \\
&=\dfrac{\partial^2}{\partial t^2}y_0(t,\varepsilon t)+2\varepsilon\dfrac{\partial}{\partial t}\dfrac{\partial}{\partial \tau}
y_0(t,\varepsilon t)+\varepsilon^2\dfrac{\partial^2}{\partial \tau^2}y_0(t,\varepsilon t).
\end{aligned}$$
> 
> 不过我们不考虑$\varepsilon^2$项, 故省略掉

我们需要找$y_0,y_1,\cdots$使得上述方程对尽可能高阶的项成立(当$\tau=\varepsilon t$时). 【注：把上式关于$\varepsilon$看作多项式,
那么使得$\varepsilon^k$中的$k$最小的项叫做主项(leading order term). 例如上式的主项是常数项.】

在多尺度分析中, 一个基本的想法就是让上述方程不仅仅对$\tau=\varepsilon t$成立, 而是对所有$\tau$都成立.
这样, 我们比较$(1.2)$的$O(1)$项和$O(\varepsilon)$项可得

$$\begin{aligned}
&\dfrac{\partial^2y_0}{\partial t}(t,\tau)+y_0(t,\tau)=0, \\
&\dfrac{\partial^2y_1}{\partial t}+y_1=-2\dfrac{\partial^2y_0}{\partial t\partial\tau}-y_0, \\
\end{aligned}$$

第一条式子可以直接解出来$y_0(t,\tau)=C_1(\tau)\cos t+C_2(\tau)\sin t$. 代入到第二条式子可得

$$\dfrac{\partial^2y_1}{\partial t}+y_1=(2C_1'(\tau)-C_2(\tau))\sin t-(2C_2'(\tau)+C-1(\tau))\cos t.$$

如果$\sin t$和$\cos t$前的系数不为0, 则在$y_1$中就会有形如$t\cos t$的项. 但是我们假设$y$可以分解成两个时间尺度(快尺度$t$和慢尺度$\tau$)时,
总是要假设所有低阶项都关于快尺度$t$呈次线性增长, 因为我们需要让主项作为主导项.
(通常如果要寻找方程, 那么就通过这个方式来找. 我们把线性增长或超线性增长的项叫做长期项(secular term). )

所以, 我们需要让上式中$\sin t$和$\cos t$前的系数为0, 不然$y_1$中就会出现线性增长的$t\cos t$和$t\sin t$. 所以

$$\begin{aligned}
&2C_1'(\tau)-C_2(\tau)=0, \\
&2C_2'(\tau)+C_1(\tau)=0.
\end{aligned}$$

于是解得

$$\begin{aligned}
C_1(\tau)&=A_1\cos\dfrac{\tau}{2}+A_2\sin\dfrac{\tau}{2}, \\
C_2(\tau)&=-A_1\sin\dfrac{\tau}{2}+A_2\cos\dfrac{\tau}{2}.
\end{aligned}$$

结合初始条件$y_0(0,0)=1$, $y_0'(0,0)=0$, 可以解得$A_1=1$, $A_2=0$. 于是

$$\tilde{y}(t)=\cos\dfrac{\varepsilon t}{2}\cos t-\sin\dfrac{\varepsilon t}{2}\sin t=\cos\left((1+\dfrac{\varepsilon}{2})t\right).$$

从而$\tilde{y}$可以在$O(1/\varepsilon)$时间尺度上逼近原问题的解.

如果我们对更长的时间尺度感兴趣, 可以把上述渐近分析推广到更高阶. 这是Poincare-Lighthill-Kuo(PLK)方法.

# 2 椭圆方程的均匀化

考虑问题

$$-\nabla\cdot(a^{\varepsilon}(x)\nabla u^{\varepsilon}(x))=f(x), x\in\Omega\subset\mathbb{R}^d.$$

边界条件为$u^{\varepsilon}|_{\partial\Omega}=0$, 系数$a^{\varepsilon}(x)=a(x,\dfrac{x}{\varepsilon})$,
其中, $a(x,y)$关于$y$是周期为$\Gamma=[0,1]^d$的函数. 为了让这个问题是椭圆问题, 需要假设存在一个与$\varepsilon$无关的常数$\alpha>0$使得

$$a^{\varepsilon}(x)\succeq \alpha I.$$

下文中涉及到的$x,y$都是$d$维向量: $x=(x_1,\cdots,x_d)^T$, $y=(y_1,\cdots,y_d)^T$.

我们假设有如下的多尺度展开:

$$u^{\varepsilon}(x)\sim u_0\left(x,\dfrac{x}{\varepsilon}\right)+\varepsilon u_1\left(x,\dfrac{x}{\varepsilon}\right)
+\varepsilon^2u_2\left(x,\dfrac{x}{\varepsilon}\right)+\cdots$$

其中函数$u_j(x,y), j=0,1,2,\cdots$关于$y$是周期为$\Gamma=[0,1]^d$的函数. 利用链式法则,

$$\dfrac{\partial}{\partial \boldsymbol{x}}u_0\left(x,\dfrac{x}{\varepsilon}\right)
=\nabla_xu_0\left(x,\dfrac{x}{\varepsilon}\right)+\dfrac{1}{\varepsilon}\nabla_yu_0\left(x,\dfrac{x}{\varepsilon}\right),$$

把多尺度展开代入原问题, 可得

$$\begin{aligned}
&\dfrac{1}{\varepsilon^2}\nabla_y\cdot\left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_yu_0\left(x,\dfrac{x}{\varepsilon}\right)\right) \\
+&\dfrac{1}{\varepsilon}\left[\nabla_y\cdot \left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_xu_0\left(x,\dfrac{x}{\varepsilon}\right)\right)
+\nabla_x\cdot\left(a\nabla_yu_0\left(x,\dfrac{x}{\varepsilon}\right)\right)
+\nabla_y\cdot\left(a\nabla_yu_1\left(x,\dfrac{x}{\varepsilon}\right)\right)
\right] \\
+&\nabla_y\cdot \left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_xu_1\left(x,\dfrac{x}{\varepsilon}\right)\right)
+\nabla_x\cdot \left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_yu_1\left(x,\dfrac{x}{\varepsilon}\right)\right) \\
+&\nabla_y\cdot \left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_yu_2\left(x,\dfrac{x}{\varepsilon}\right)\right)
+\nabla_x\cdot \left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_xu_0\left(x,\dfrac{x}{\varepsilon}\right)\right)+\cdots=-f(x). \\
\end{aligned}$$

比较主项可得

$$-\nabla_y\cdot\left(a\left(x,\dfrac{x}{\varepsilon}\right)\nabla_yu_0\left(x,\dfrac{x}{\varepsilon}\right)\right)=0.$$

这对$y=x/\varepsilon$成立, 但是类似前面的ODE的情形我们让它对所有的$x,y$都成立:

$$-\nabla_y\cdot(a(x,y)\nabla_yu_0(x,y))=0.$$

利用椭圆问题的先验估计(参见Gilbarg-Trudinger书), 可得$u_0$与$y$无关, 从而

$$u_0=u_0(x).$$

比较$\dfrac{1}{\varepsilon}$项可得

$$-\nabla_y\cdot(a(x,y)\nabla_yu_1(x,y))=\nabla_y\cdot(a(x,y)\nabla_xu_0(x)). \tag{1.3}$$

这是关于$u_1$的PDE, 并且把$\nabla_xu_0$看作(与$y$无关的)常数. 为了求解这个问题, 我们引入cell problem:

$$-\nabla_y\cdot(a(x,y))\nabla_y\chi^j)=\nabla_y\cdot(a(x,y),e_j).$$

其中$e_j=(0,\cdots,0,1,0,\cdots,0)$在第$j$个分量是1, 其余分量是0.
(cell problem的中文翻译暂时不知道, 不过可以理解为把一个大的问题分成$d$个小的问题.)

记$\chi=(\chi^1,\cdots,\chi^d)$. 那么我们可以把$u_1$表示成

$$u_1(x,y)=\chi(x,y)\cdot \nabla_xu_0(x). \tag{1.4}$$

结合cell problem以及上式可以验证$(1.3)$的确成立.

再比较$O(1)$的项, 可得

$$\begin{aligned}
&\nabla_y\cdot \left(a\left(x,y\right)\nabla_yu_2\left(x,y\right)\right)
+\nabla_y\cdot \left(a\left(x,y\right)\nabla_xu_1\left(x,y\right)\right) \\
+&\nabla_x\cdot \left(a\left(x,y\right)\nabla_yu_1\left(x,y\right)\right) \\
+&\nabla_x\cdot \left(a\left(x,y\right)\nabla_xu_0\left(x\right)\right)+\cdots=-f(x). \\
\end{aligned} \tag{1.5}$$

这是关于$u_2$的方程. 为了求出周期解, $u_0,u_1$需要满足一定的可求解性条件. 我们定义关于快变量$y$的平均算子(averaging operator)如下:

$$\langle f\rangle=\int_{\Gamma=[0,1]^d}f(y)\mathrm{d}y=\overline{f}.$$

把这个算子作用在$(1.5)$的两侧可得

$$\nabla_x\cdot(\langle a(x,y)\nabla_yu_1\langle x,y\rangle)
+\nabla_x(\langle a(x,y)\rangle\nabla_xu_0(x))=-f(x). \tag{1.6}$$

(注意利用散度定理以及周期性条件, 我们可以消掉关于$y$求散度的项. )

利用$(1.4)$式可得

$$a(x,y)\nabla_yu_1(x,y)=a(x,y)\nabla_y(\chi(x,y)\nabla_xu_0(x)),$$

所以

$$\nabla_x\cdot(\langle a\nabla_y\chi+a\rangle \nabla_xu_0)=-f.$$

下面我们定义矩阵

$$A(x)=\langle a(x,y)(I+\nabla_y\chi(x,y))\rangle.$$

这样, 我们就能得到关于$u_0$的**均匀化方程(homogenized equation)**:

$$\boxed{-\nabla\cdot(A(x)\nabla u_0(x))=f(x)}.$$

举个例子, 对于一维情形, $d=1$, 此时$x,y$是数量(而不是向量), 从而cell problem变成了

$$-\partial_y(a(x,y)\partial_y\chi)=\partial_ya(x,y).$$

对两边取关于$y$的不定积分, 可得

$$a(x,y)(1+\partial_y\chi)=C_0.$$

($C_0=C_0(x)$. )两边同除以$a(x,y)$然后取平均, 利用$\chi$在$[0,1]$上的周期性可得

$$1=\left\langle\dfrac{C_0}{a}\right\rangle=C_0(x)\int_0^1\dfrac{1}{a(x,y)}\mathrm{d}y.$$

于是我们得到了

$$A(x)=C_0=\left\langle\dfrac{1}{a}\right\rangle^{-1}.$$

注意$C_0$是$a(x,y)$的调和平均, 通常它不等于算术平均, 即$C_0\ne \int_0^1a(x,y)\mathrm{d}y$.

# 3 变分形式问题的多尺度检验函数

椭圆方程可以写成变分形式(或者弱形式), 这时可以得到弱解. 而我们也可以在弱解的意义下去思考多尺度问题.
基本的想法是把多尺度检验函数拆分成不同的尺度.

{: .theorem }
> **引理(Nguetseng, 1989)** 设$\lbrace u^{\varepsilon}\rbrace $是一列在$L^2(\Omega)$中一致有界函数, 即$\|u^{\varepsilon}\|_{L^2}\le C$.
则存在子列$\lbrace u^{\varepsilon_j}\rbrace $与函数$u\in L^2(\Omega\times\Gamma), \Gamma=[0,1]^d$, 使得对$\varepsilon_j\to 0$, 有
> 
> $$\int u^{\varepsilon_j}(x)\varphi\left(x,\dfrac{x}{\varepsilon}\right)\mathrm{d}x
\to\iint u(x,y)\varphi(x,y)\mathrm{d}x\mathrm{d}y$$
> 
> 对任意$\varphi\in C(\Omega\times\Gamma)$满足它关于$y$是周期为$\Gamma$的函数都成立.


为了用这个引理, 我们把原来的问题$-\nabla\cdot(a^{\varepsilon}(x)\nabla u^{\varepsilon}(x))=f(x)$改写为

$$\boldsymbol{w}^{\varepsilon}=\nabla u^{\varepsilon}, -\nabla\cdot(a^{\varepsilon}(x)\boldsymbol{w}^{\varepsilon}(x))=f(x).$$

它的弱形式就是

$$\int_{\Omega}a^{\varepsilon}(x)\boldsymbol{w}^{\varepsilon}(x)\nabla \varphi^{\varepsilon}(x)\mathrm{d}x
=\int_{\Omega}f(x)\varphi^{\varepsilon}(x)\mathrm{d}x.$$

考虑检验函数形如$\varphi^{\varepsilon}(x)=\varphi_0(x)+\varepsilon_1(x,x/\varepsilon)$, 我们有

$$\begin{aligned}
\int_{\Omega}a\left(x,\dfrac{x}{\varepsilon}\right)\boldsymbol{w}^{\varepsilon}(x)
\left[\nabla_x\varphi_0(x)+\nabla_y\varphi_1\left(x,\dfrac{x}{\varepsilon}\right)
+\varepsilon\nabla_x\varphi_1\left(x,\dfrac{x}{\varepsilon}\right)\right]\mathrm{d}x \\
=\int_{\Omega}f(x)\left(\varphi_0(x)+\varepsilon\varphi_1\left(x,\dfrac{x}{\varepsilon}\right)\right)\mathrm{d}x.
\end{aligned}$$

利用引理, 可知存在函数$\boldsymbol{w}\in L^2(\Omega\times\Gamma)$, 使得

$$\iint_{\Omega\times\Gamma}a(x,y)\boldsymbol{w}(x,y)(\nabla_x\varphi_0(x)+\nabla_y\varphi_1(x,y))\mathrm{d}x\mathrm{d}y
=\int_{\Omega}f(x)\varphi_0(x)\mathrm{d}x.$$

在上式令$\varphi_1=0$, 那么可以得到

$$-\nabla_x\cdot\langle a\boldsymbol{w}\rangle=f. \tag{1.7}$$

在上式令$\varphi_0=0$, 那么可以得到

$$\nabla_y\cdot(a\boldsymbol{w})=0. \tag{1.8}$$

由于$\boldsymbol{w}^{\varepsilon}=\nabla u^{\varepsilon}$, 于是

$$\int_{\Omega}\boldsymbol{w}^{\varepsilon}(x)\varphi^{\varepsilon}(x)\mathrm{d}x
=-\int_{\Omega}u^{\varepsilon}(x)\nabla\varphi^{\varepsilon}(x)\mathrm{d}x.$$

同样用上面的检验函数, 然后结合引理, 可得存在$u\in L^2(\Omega\times\Gamma)$使得

$$\iint_{\Omega\times\Gamma}\boldsymbol{w}(x,y)\varphi_0(x)\mathrm{d}x\mathrm{d}y
=-\iint_{\Omega\times\Gamma}u(x,y)(\nabla_x\varphi_0(x)+\nabla_y\varphi_1(x,y))\mathrm{d}x\mathrm{d}y.$$

在上式令$\varphi_0=0$, 那么可以得到
$\iint_{\Omega\times\Gamma}u(x,y)\nabla_y\varphi_1(x,y)\mathrm{d}x\mathrm{d}y=0$
对任意$\varphi_1$成立, 所以$\nabla_yu=0$. 从而$u(x,y)=u_0(x)$.

在上式令$\varphi_1=0$, 那么可以得到

$$\langle \boldsymbol{w}\rangle=-\nabla_x\langle u\rangle=-\nabla_xu_0.$$

注意梯度的旋度为0, 所以$\nabla\times \boldsymbol{w}^{\varepsilon}=0$, 同样对这个式子用前面的各种操作, 可得存在$u_1\in H^1(\Omega\times\Gamma)$, 使得

$$\boldsymbol{w}(x,y)=\nabla_yu_1(x,y)+\nabla_xu_0(x).$$

把它代入$(1.7)$$(1.8)$, 可得

$$\left\lbrace \begin{aligned}
&-\nabla_y\cdot(a(\nabla_yu_1+\nabla_xu_0))=0, \\
&-\nabla_x\cdot\langle a(\nabla_yu_1+\nabla_xu_0)\rangle=f.
\end{aligned}\right.$$

上式与前面的均匀化问题等价, 分别对应$(1.3)$与$(1.6)$式.


