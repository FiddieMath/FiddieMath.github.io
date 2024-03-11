---
layout: default
title: 特征值问题：【实例】谷歌PageRank算法简介
parent: 数值计算方法
grand_parent: 助教工作
nav_order: 401
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

# PageRank算法

PageRank算法是对网页排名的算法, 曾是Google发家致富的法宝. 

PageRank算法是在一个有向图上的顶点赋予“排名(rank)”的算法,
它的应用场景是搜索引擎, 例如我们熟知的Google、Bing、百度等等.
我们把互联网上的不同网页看成一个个顶点, 
而有向图中从顶点$i$到顶点$j$则表示从网页$i$存在着到网页$j$的超链接.

考虑有向图$G(V,E)$, 顶点为$V=\lbrace 1,\cdots,n\rbrace$, 边集为$E$. 有向图可用邻接矩阵$\mathbf{A}\in\lbrace 0,1\rbrace^{n\times n}$来表示,
其分量如下给出:

$$a_{ij}=\left\{\begin{aligned}
&1, &&\text{若存在从$i$到$j$的边}, \\
&0, &&\text{若不存在从$i$到$j$的边}.
\end{aligned}\right.$$

记$r_i$表示指定在顶点$i$上的一个“值”. PageRank算法的最简单的思想, 是通过求解如下线性方程组来把一些值指定在顶点上:

$$\forall i\in V, \qquad r_i=\sum\limits_{j\in\mathcal{N}(i)}\dfrac{r_j}{o_j}. $$

其中, $o_j$是$j$的外度(outdegree), 即从顶点$j$指向其他顶点的有向边的个数.
$\mathcal{N}(i)$表示指向$i$的相邻点的全体, 即$j\in\mathcal{N}(i)$当且仅当存在一条从顶点$j$指向顶点$i$的有向边.

{: .problem}
> **问题1.** 搜索PageRank算法进行进一步了解.

可参考[知乎文章：PageRank算法详解](https://zhuanlan.zhihu.com/p/137561088)

## 问题

{: .problem}
> **问题2.** 设$\boldsymbol{r}=(r_1,\cdots,r_n)^T$, 证明$\boldsymbol{r}$满足
>
> $$\boldsymbol{r}=\mathbf{A}^T \mathbf{O}^{-1}\boldsymbol{r},$$
>
> 其中, $\mathbf{O}=\mathrm{diag}(\tfrac{1}{o_1},\cdots,\tfrac{1}{o_n})$. 
>
> 换言之, 这里要我们证明的结论是$\boldsymbol{r}$是矩阵$\mathbf{M}=\mathbf{A}^T \mathbf{O}^{-1}$的特征值1对应的特征向量.
>
> **问题3.** 证明矩阵$\mathbf{M}$是**左随机的(left-stochastic)**, 即$\mathbf{M}$的每一列之和都是$1$.
>
> **问题4.** 证明$\rho(\mathbf{M})=1$并给出一个范数$\Vert\cdot\Vert$使得$\Vert\mathbf{M}\Vert = 1$. 

接下来我们写程序. 可以发现, PageRank算法本质上就是要找矩阵$\mathbf{M}$的一个特征向量, 所以需要用特征值的算法. 

{: .problem}
> **问题5.** 用PageRank算法对英文维基百科的2013年的快照进行页面的排序.  
> 你可以考虑用上面的简化版的算法, 也可以用你搜寻到的一些改进的PageRank算法. 
>
> 简化版算法的迭代终止准则可采用下面两种之一:
>
> - $\dfrac{\Vert\mathbf{M}\widehat{\boldsymbol{r}} - \widehat{\boldsymbol{r}}\Vert_1}{\Vert\widehat{\boldsymbol{r}}\Vert_1} < 10^{-15}$
> - $\dfrac{\Vert\mathbf{M}\widehat{\boldsymbol{r}} - \widehat{\lambda}\widehat{\boldsymbol{r}}\Vert_1}{\Vert\widehat{\boldsymbol{r}}\Vert_1} < 10^{-15}$, 其中, $\widehat{\lambda} = \dfrac{\widehat{\boldsymbol{r}}^T\mathbf{M}\widehat{\boldsymbol{r}}}{\widehat{\boldsymbol{r}}^T\widehat{\boldsymbol{r}}}.$
>
> 其中, $\widehat{\boldsymbol{r}}$是最大特征值对应的特征向量的一个逼近值.
>
> 附件：[2013年快照的数据集](/res/data_pagerank.rar).
>
> (1)打印出前10个排序最高的网页.
>
> (2)写一个“搜索引擎”程序，用于搜索所有包含某个关键词的网页, 比如搜索“New York”就会得到所有包含“New York”的网页. 
> 网页顺序最好按照之前求出来的$\boldsymbol{r}$来作排序. 

## 附录：代码

建议用Jupyter Notebook运行.
需要把上面压缩文件里面的两个csv文件和你的python代码文件放在同一个目录

### 导入文件

导入csv文件的代码如下. 这里涉及到用Python作数据分析的问题, 可以考虑使用Pandas包.

{: .remark}
> Pandas包是一个强大的分析结构化数据的工具集; 它的使用基础是Numpy （提供高性能的矩阵运算）;
> 用于数据挖掘和数据分析, 同时也提供数据清洗功能. 
>
> 如果同学们以后想走统计方向, 对数据分析的了解和基本工具使用都是必不可少的. 

```python
import numpy as np
import pandas as pd

nodes = pd.read_csv('names.csv')  #获取所有的网页名称
nodes.values 

n = len(nodes)   #网页名称的数量
print(n)         #输出：199903

nodes.head() #前5条网页名称

edges.head() #前5条“有向边”

m = len(edges)   #有向边的数量
print(m)         #输出：10722190

```

### 用稀疏矩阵求解

这里数据非常庞大，我们需要用自带的稀疏矩阵的工具来求解.

```python
import scipy.sparse as sparse
from scipy.sparse.linalg import spsolve

A = sparse.lil_matrix((n,n)) #Sparse matrix
o = np.zeros(n) #vector o

for i in range(m):
    A[edges['FromNode'][i] - 1,edges['ToNode'][i] - 1] = 1
    o[edges['FromNode'][i] - 1] += 1
    if(i%100000==0):  #每100000次输出一下
        print(i, end='\t', flush=True)

A = sparse.csr_matrix(A)             #转化为便于作矩阵运算的稀疏矩阵格式
AT = sparse.csr_matrix.transpose(A)  #转置

oinv = 1. / o
Oinv = sparse.spdiags(oinv, 0, n, n) #求$diag(o_i^{-1})$

M = AT @ Oinv                        #用@表示矩阵的乘法

def eigs(A, dim, p):                 #用Arnoldi方法求稀疏矩阵特征值和特征向量
    n = dim
    u = np.ones([n,p+1]) 
    u[:,0] = np.ones(n)/n
    h = np.zeros([p+1,p+1])   #若p很大：用sparse.lil_matrix((p+1,p+1))
    for j in range(p):
        u[:,j+1] = A@u[:,j]
        for i in range(j+1):
            h[i][j] = np.dot(u[:,i], u[:,j+1])
            u[:,j+1] = u[:,j+1] - h[i][j] * u[:,i]
        h[j+1][j] = np.linalg.norm(u[:,j+1], 1)
        if(h[j+1][j] < 1e-15 or np.linalg.norm(A@u[:,j+1]-u[:,j+1],1)/np.linalg.norm(u[:,j+1],1) < 1e-15):
            break
        u[:,j+1] = u[:,j+1] / h[j+1][j]
        print(j, end='\t', flush=True)
    egvec = u[:,j+1]
    egval = np.dot(egvec, (A@egvec)) / np.dot(egvec,egvec)
    # Return eigenvalue and eigenvector
    return egval,egvec

eigenvalues, eigenvectors = eigs(M, n, 20) #执行20步Arnoldi迭代

print(eigenvalues)                         #输出特征值，输出结果：0.9999292040726496

print(eigenvectors)                        #输出特征向量

tmp_eigenvectors = eigenvectors.copy()     #求特征向量的前10个最大分量
for i in range(10):
    maxRank = np.amax(tmp_eigenvectors)
    idx = np.where(tmp_eigenvectors == maxRank)
    print(i+1, nodes['Name'][idx[0][0]], maxRank)
    tmp_eigenvectors[idx] = 0

```

输出结果：

```
1 United States 0.002499397134480645
2 United Kingdom 0.001396196448521341
3 World War II 0.001135828080408877
4 Latin 0.0010844306312105254
5 France 0.00108092383560689
6 Germany 0.0009214380521730097
7 English language 0.0008398701285453095
8 China 0.0007998402774034384
9 Canada 0.0007949766932128825
10 India 0.000791633158794371
```

### 寻找关键词

如果要寻找一个列表的关键词，可调用如下的```search```函数：

```python
def search(keyword):
    for i in range(n):
        if(type(nodes['Name'][i])==str):
            if(nodes['Name'][i].__contains__(keyword)):
                print(nodes['Name'][i])
```

