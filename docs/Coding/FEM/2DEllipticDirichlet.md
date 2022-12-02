---
layout: default
title: 二维椭圆方程(Dirichlet边界)
parent: 有限元
grand_parent: 代码记录
nav_order: 11
---

更新日期：2022年12月2日

{: .new}
> 未完成

{: .no_toc }

<details open markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

# 引言

所有研究有限元的同学必定会先接触二维椭圆方程, 但是在写代码方面, 此前我只是停留在Matlab的调包当中. 就比如, 考虑问题

$$-\mathrm{div}(\nabla u)=4, \text{ in }\Omega=(0,1)\times(0,1),$$

其中边界条件为

$$u|_{\partial\Omega}=0,$$

那么用Matlab的PDE ToolBox就是

```
g=[2,2,2,2; 0,1,1,0; 1,1,0,0; 1,1,0,0; 1,0,0,1; 0,0,0,0; 1,1,1,1];  %区域 
n = 8; %网格大小
[p,e,t]=poimesh(g,n); 

pdemesh(p,e,t);              %画网格
xlim([0 , 1])
ylim([0 , 1])
axis equal;

c=1; a=0; f=4; 
b = 'circleb1';              %Dirichlet零边界
u=assempde(b,p,e,t,c,a,f);
pdesurf(p,t,u);              %画解
```

非常的简单. 但是要是想深入了解有限元方法实现, 还是需要自己动手去做. 
由于目前的研究需要, 我现在要用Python来实现二维椭圆方程的求解.

## 问题

求解

$$-\mathrm{div}(c\nabla u)=f, \text{ in }\Omega,$$

其中边界条件为

$$u|_{\partial\Omega}=g.$$

采用三角网格.

## 基本步骤

设计程序的基本步骤是：

- 定义结点、边、有限元包含的结点

- 装配稀疏矩阵

- 求解稀疏线性方程组

- 分析数值解、画图等等.

我们先从最简单的三角网格做起. 
设区域为$\Omega=(0,1)\times(0,1)$, 把$(0,1)$区间等分成$n$份, 每个小区间长为$h=\dfrac{1}{n}$. 构造网格如下图:

<div align = center>
<img src="/pics/pdemesh1.png" width = "400"/>

<br/>

图1：网格($n=16$的情形)
</div>

# 程序实现

## 网格生成

### 定义结点

一个网格包含很多结点, 每一行有$n+1$个结点, 我们把结点从下到上、左到右编号. 

第0个结点坐标为$(0,0)$的点, 第$n$个结点坐标为$(1,0)$, 第$n+1$个结点坐标为$(h,0)$, $\cdots$, 
第$(n+1)^2-1$个结点坐标为$(1,1)$. 如下图.

<div align = center>
<img src="/pics/pdemesh2.png" width = "400"/>

<br/>

图2：结点编号($n=16$的情形)
</div>

我们把结点编号对应的坐标存储在信息矩阵(information matrix) `Pb` 中. 

```python
    #结点与真实坐标的对应关系，存储在information matrix Pb 中
    Nb = (n+1)*(n+1) #number of nodes
    Pb = {} #{}表示一个空的字典
    for j in range(n+1):
        for i in range(n+1):
            Pb[i+j*(n+1)]=np.array([i/n,j/n])
```

### 定义边

我们目前还没考虑Neumann边界条件, 暂时先不考虑边的定义(暂时用不上).

### 定义有限元

每个有限元区域$K$由三个顶点构成, 所以我们只需要存储三个顶点的编号即可.

在第一次写这个部分的时候, 建议把直角对应的顶点放在第一个.

同样, 我们从下到上、从左到右存储, 这里一共有$2n^2$个elements. 

<div align = center>
<img src="/pics/pdemesh3.png" width = "300"/>

<br/>

图2：有限元编号(局部)
</div>


```python
    Nlb = 3             #number of nodes on each element
    N = 2*n*n           #number of elements
    Tb = np.zeros((N, 3), dtype=np.int32)
    for i in range(n):
        for j in range(n):
            #第ij个单元的结点按顺序是i+(n+1)j, i+1+(n+1)j, i+1+n+(n+1)j.
            Tb[i+j*n*2]=[i+(n+1)*j, i+1+(n+1)*j, i+1+n+(n+1)*j]

            #第ij个单元的结点按顺序是i+2+n+(n+1)j, i+1+(n+1)j, i+1+n+(n+1)j.
            Tb[i+j*n*2+n]=[i+2+n+(n+1)*j, i+1+(n+1)*j, i+1+n+(n+1)*j] 
```

### 定义边界结点

对于边界结点，我们需要指定边界类型和边界点的编号. 
边界类型中，用1表示Dirichlet边界条件，2表示Neumann边界条件(后面再用到), 3表示Robin边界条件(后面再用到).

边界结点不用讲究存储顺序.

```python
    Nbn = 4*n         #number of boundary nodes
    bdnodes = np.zeros((Nbn, 2), dtype=np.int32)
    for i in range(n):
        bdnodes[i][0] = 1                 #Dirichlet
        bdnodes[i][1] = i
        bdnodes[i+n][0] = 1               #Dirichlet
        bdnodes[i+n][1] = n + (n+1)*i
        bdnodes[i+2*n][0] = 1             #Dirichlet
        bdnodes[i+2*n][1] = (n+1) * (i+1)
        bdnodes[i+3*n][0] = 1             #Dirichlet
        bdnodes[i+3*n][1] = n*n+n+i+1
```

至此, 关于网格的构造已经完成. 

## 装配矩阵和右端向量

注意装配的矩阵是稀疏的, 所以我们要引入稀疏矩阵的包.

```python
import scipy.sparse as sparse
from scipy.sparse.linalg import spsolve
```

首先用```lil_matrix```来初始化一个稀疏矩阵：

```python
    A = sparse.lil_matrix((Nb,Nb)) #稀疏矩阵
```

{: .remark}
> 关于稀疏矩阵的多种存储方式(不止```lil_matrix```)可以在别处搜到.

如果$c$是一个常数, 那么我们可以很快手动算出单刚度矩阵$S=(s_{ij})$是

$$S=c\begin{pmatrix}
1&-0.5&-0.5 \\ -0.5 & 0.5 & 0 \\ -0.5 & 0 & 0.5
\end{pmatrix},$$

其中, 

$$s_{ij} = \int_{K}c\nabla\varphi_i\cdot\nabla\varphi_j\mathrm{d}x\mathrm{d}y,$$

这里$K$是由$A_0(0,0)$, $A_1(1,0)$, $A_2(0,1)$构成的参考单元.
节点基函数为$\phi_0(x,y)=1-x-y$, $\phi_1(x,y)=x$, $\phi_2(x,y)=y$. 作旋转、平移变换之后得到的结果也是$S$. 

{: .remark}
> 这就是为什么我们一开始要求直角对应的结点必须放在第1个位置, 不然的话$S$的某些行和某些列会发生互换.

算完之后把单刚度矩阵拼接成总刚度矩阵即可. (注意下面的```Nlb```为$3$.)


```
    S = np.array([[1,-0.5,-0.5],
              [-0.5,0.5,0],
              [-0.5,0,0.5]  ]) #单刚度矩阵

    for k in range(N):  #第k个单元      
        for i in range(Nlb): #第i个结点
            for j in range(Nlb): #第j个结点
                r = c*S[j][i] #单刚度矩阵
                A[Tb[k][j],Tb[k][i]] += r
```


如果$c$不是一个常数, 而是一个函数, 那么这就比较复杂了. 此时计算$s_{ij}$需要用到数值积分, 并且单刚度矩阵$S$不尽相同. 
我们先用```localstiff```来表示从给定三个结点构造单刚度矩阵的函数, 后续再补充. 

```
    for k in range(N):  #第k个单元  
        p = np.array([Pb[Tb[k][0]], Pb[Tb[k][1]], Pb[Tb[k][2]]])  
        S = localstiff(p, c)
        for i in range(Nlb): #第i个结点
            for j in range(Nlb): #第j个结点
                r = S[j][i] #单刚度矩阵
                A[Tb[k][j],Tb[k][i]] += r
```

右端向量的第$i$个分量就是(其中$E_n$表示第$n$个单元)

$$\int_{\Omega}f\phi_i\mathrm{d}x\mathrm{d}y=\sum\limits_{n=1}^N \int_{E_n}f\phi_i\mathrm{d}x\mathrm{d}y,$$
