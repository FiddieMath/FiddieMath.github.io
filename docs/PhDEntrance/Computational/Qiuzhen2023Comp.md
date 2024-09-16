---
layout: default
title: 2023求真书院
parent: 计算数学
grand_parent: 博资考真题
nav_order: 10012023
---

# 求真书院 2023 博资考试题

Date: September 2023

## Problem 1

Consider the Newton's method for finding a solution $x _ *$ to $f(x)=0$, where $f\in C^2(a,b)$, $x _ *\in(a,b)$.

```matlab
determine $x_0\in(a,b)$.
for k=0,1,2,... do
  $x_{k+1}=x_k-\dfrac{f(x_k)}{f'(x_k)}$.
end for
```

(1). Prove that if $x _ 0$ is sufficiently close to $x _ *$ and $f'(x _ *)\ne 0$, then $\lim\limits _ {k\to\infty} x _ k=x _ *$ and $\lim\limits_{k\to\infty}\dfrac{x _ {k+1}-x _ *}{(x _ k-x _ *)^2}=\dfrac{f^{\prime\prime}(x _ *)}{2f'(x _ *)}.$

(2). In practice sometimes the derivative is not easy to be obtained. As a result, a difference is used instead: $x_ {k+1}=x_ k-\dfrac{x_ k-x_ {k-1}}{f(x _ k)-f(x _ {k-1})}f(x _ k)$. Prove that if $x_0$ is sufficiently close to $x_ *$, then $x_ k \to x_ *$ and $\lim\limits_ {k\to\infty} \dfrac{x_ {k+1}-x _ * }{(x_ k-x_ *)(x_ {k-1}-x_ *)}=\dfrac{f^{\prime\prime}(x_ *)}{2f'(x _ *)}.$

## Problem 2

Consider the explicit shifted QR method for computing eigenvalues of a matrix $A\in\mathbb{C}^{n\times n}$. 

```matlab
Find an upper Hessenberg matrix $H_0$ and a unitary matrix $U_0$ such that $H_0=U_0^HAU_0$. 
for i=0,1,2,... do
  Determine a scaler $\mu_k$. 
  Compute QR factorization $Q_kR_k = H_k-\mu_k I$.
  $H_{k+1} = R_kQ_k + \mu_k I$.
end for
```

(1). Prove that $H_i$, $i=1,2,\cdots$ are all upper Hessenberg matrices. 

(2). Interpret the purpose to use $H_0$ rather than $A$ in the iteration.

(3). Suppose that $A$ has $n$ distinct eigenvalues and none of the shifts $\mu_i$, $i=1,2,\cdots$ is an eigenvalue of $A$. Prove that $H_i$, $i=0,1,2,\cdots$ are unreduced upper Hessenberg matrices. (An upper Hessenberg matrix $H$ is called unreduced, if $H _ {i+1,i}\ne 0$ for $i=1,\cdots,n-1$. )

(4). Write 

$$H_k=\begin{bmatrix} G_k & u_k \\ \varepsilon_ke^T & \alpha_k \end{bmatrix}$$ 

when $\alpha_k,\varepsilon_k\in \mathbb{C}$, $u_k,e\in\mathbb{C}^{n-1}$ and 

$$e=\begin{bmatrix} 0 \\ \vdots \\ 0 \\ 1 \end{bmatrix}$$

Suppose $A$ has $n$ distinct eigenvalues. Prove that $\vert\varepsilon_ {k+1}\vert \le \rho_k^2 \Vert u _ k\Vert _ 2 \vert \varepsilon _ k\vert ^2 + \rho _ k \vert \alpha _ k -\mu _ k\vert \vert \varepsilon _ k \vert$, where $\rho _ k = \Vert (G _ k)-\mu _ k I )^{-1}\Vert _ 2$, provided $\mu _ k$ is not an eigenvalue of $G _ k$.

## Problem 3

If $p$ is a polynomial of degree $n$ (on $[-1,1]$ ), it is determined by its values on an $(n+1)$ - point grid on $[-1,1]$. The derivative $p'$, a polynomial of degree $(n-1)$, is determined on the same grid. The (classical) differentiation matrix is the $(n+1)$ - by - $(n+1)$ matrix $D=(D_{ij})\in \mathbb{R}^{(n+1)\times(n+2)}$ that represents the linear map from the vector of values of $p$ to the vector of values of $p'$, namely:

$$
p'(x _ i)=\sum\limits _ {j=0}^n D_{ij} p(x _ j).
$$

(1). Prove that $D_ {ij} = l_j'(x_i)$, where $l_ j (x)$ is the $j$ - th Lagrange basis function.

(2). If a Chebyshev grid $(x_j=\cos(j\pi/n), 0\le j\le n)$ is adopted, derive explicit formulas for $D_ {ij}$.

## Problem 4

Consider a Runge-Kutta method for the ODE $y'=f(t,y)$ ( $f$ is Lipschitz continuous in $y$ and uniform in $t$) with the following Butcher tableau:

$$
\begin{array}{c|cc}
0 & 0 \\
1 & 1 & 0 \\ \hline
 & 1/2 & 1/2
\end{array}
$$

(1). Rewrite the scheme in the form of $u _ {n+1}=u _ n+hF(t _ n,u _ n,h;f)$.

(2). Assume that $f$ is sufficiently smooth. Prove that this method is convergent and determine the order of convergence.

(3). What is the region of absolute stability of this method? Give a description that is as explicit as possible.

## Problem 5

For the equation $u_ t+au_ {xxx} = 0$ ($a$ is a constant), applying the idea of the Lax-Friedrichs scheme, one can get the scheme

$$
u_m^{n+1}=\dfrac{1}{2}(u_ {m+1}^n + u _{m-1}^n)
-\dfrac{1}{2}akh^{-3} (u_ {m+2}^n - 2u _ {m+1}^n + 2u _ {m-1}^n - u _ {m-2}^n),
$$

where $k$ and $h$ represent the time step and mesh size, respectively.

(1). Give the leading order term of local truncation error.

(2). Analyze the stability of this scheme.

## Problem 6

Consider the following linear programming problem

$$
\max\limits_{\bf{x}}\langle\mathbf{c},\mathbf{x}\rangle \quad \text{s.t.}\quad
A\bf{x}=\bf{b}, \quad \bf{x}\ge 0,
$$

where $\mathbf{x}\in\mathbb{R}^n$, $0\le \mathbf{b}\in\mathbb{R}^n$, $A\in\mathbb{R}^{m\times n}$ and $\mathbf{c}\in\mathbb{R}^n$. $A$ is a full rank matrix and $m < n$.

(1) Prove that the basic feasible solutions are equivalent to the vertices of its feasible region.

(2) Write down the dual problem, and prove that when the optimal solution exists, the dual problem must also have an optimal solution, and the optimal objective values of these two problems are equal.

## Problem 7

Consider the eigenvalue problem with $0 < \epsilon \ll 1$.

$$
\begin{aligned}
&u^{\prime\prime}+(\lambda+\epsilon f(x))u=0, \quad 0 < x < 1, \\
&u(0)=0, \quad u'(1)=0.
\end{aligned}
$$

where $f$ is a given smooth function. Give the asymptotic expansion of $\lambda$ such that the accuracy is $O(\epsilon)$.
