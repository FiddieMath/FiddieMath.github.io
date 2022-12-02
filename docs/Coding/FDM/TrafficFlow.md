---
layout: default
title: 交通流问题
parent: 有限差分
grand_parent: 代码记录
nav_order: 111
---

出处：MIT, Numerical Methods for Partial Differential Equations

# Problem Statement

Consider the traffic flow problem, described by the non-linear hyperbolic equation:

$$\dfrac{\partial \rho}{\partial t}+\dfrac{\partial\rho u}{\partial x}=0$$

with $\rho=\rho(x,t)$ the density of cars (vehicles/km), and $u=u(x,t)$ the velocity.
Assume that the velocity $u$ is given as a function of $\rho$:

$$u=u_{\max}\left(1-\dfrac{\rho}{\rho_{\max}}\right),$$

with $u_{\max}$ the maximum speed and $0\le \rho\le\rho_{\max}$. 
The flux of cars is therefore given by

$$f(\rho)=\rho u_{\max}\left(1-\dfrac{\rho}{\rho_{\max}}\right).$$

We will solve this problem using a first order finite volume scheme:

$$\rho_i^{n+1}=\rho_i^n-\dfrac{\Delta t}{\Delta x}\left(F_{i+\frac{1}{2}}^n-F_{i-\frac{1}{2}}^n\right).$$

For the numerical flux function, we will consider two different schemes:

### **(a)Roe's Scheme**

The expression of the numerical flux is given by:

$$F_{i+\frac{1}{2}}^R=\dfrac{1}{2}[f(\rho_i)+f(\rho_{i+1})]-\dfrac{1}{2}|a_{i+\frac{1}{2}}|(\rho_{i+1}-\rho_i)$$

with 

$$a_{i+\frac{1}{2}}=u_{\max}\left(1-\dfrac{\rho_i+\rho_{i+1}}{\rho_{\max}}\right).$$

Note that $a_{i+\frac{1}{2}}$ satisfies

$$f(\rho_{i+1})-f(\rho_i)=a_{i+\frac{1}{2}}(\rho_{i+1}-\rho_i).$$

### **(b)Godunov's Scheme**

In this case the numerical flux is given by:

$$F_{i+\frac{1}{2}}^G=f\left(\rho(x_{i+\frac{1}{2}}, t^{n+})\right)
=\left\{\begin{aligned}
&\min\limits_{\rho\in[\rho_i,\rho_{i+1}]}f(\rho), &&\rho_i < \rho_{i+1}, \\
&\max\limits_{\rho\in[\rho_i,\rho_{i+1}]}f(\rho), &&\rho_i > \rho_{i+1}.
\end{aligned}\right.$$

## Questions

### Question 1

For both Roe's Scheme and Godunov's Scheme, look at the problem of a traffic light
turning green at time $t = 0$. We are interested in the solution at $t = 2$ using both schemes.
What do you observe for each of the schemes? Explain briefly why the behavior you get
arises.

Use the following problem parameters:

$$\begin{aligned}
\rho_{\max}&=1.0, & \rho_L&=0.8 \\
u_{\max}&=1.0,  \\
\Delta x&=\dfrac{4}{400}, & \Delta t&=\dfrac{0.8\Delta x}{u_{\max}}.
\end{aligned}$$

The initial condition at the instant when the traffic light turns green is

$$\rho(0)=\left\{\begin{aligned}
&\rho_L, &&x < 0, \\
&0, && x\ge 0.
\end{aligned}\right.$$

### Question 2

**For the rest of this problem use only the scheme(s) which are valid models of the
problem.**

Simulate the effect of a traffic light at $x = -\dfrac{\Delta x}{2}$ 
which has a period of $T = T_1+T_2= 2$ units. 
Assume that the traffic light is $T_1= 1$ units on red and $T_2= 1$ units on green. Assume
a sufficiently high flow density of cars (e.g. set $\rho = \dfrac{\rho_{\max}}{2}$
on the left boundary - giving a
maximum flux), and determine the average flow, or capacity of cars over a time period $T$.
The average flow can be approximated as 

$$\dot{q}=\dfrac{1}{N_T}\sum_{n=1}^{N_T}f^n=\dfrac{1}{N^T}\sum_{n=1}^{N_T}\rho^nu^n,$$

where $N_T$ is the number of time steps for each period $T$.  You should run your computation
until $\dot{q}$ over a time period does not change. Note that by continuity $\dot{q}$ can be evaluated over
any point in the interior of the domain (in order to avoid boundary condition effects, we
consider only those points on the interior domain).

**Note:** A red traffic light can be modeled by simply setting $F_{i+\frac{1}{2}}=0$ at the position where
the traffic light is located.

### Question 3

Assume now that we simulate two traffic lights, one located at
$x = 0$, and the other at $x = 0.15$, both with a period $T$. Calculate the road capacity 
($=$ average flow) for different delay factors. That is if the first light turns green at time $t$, then
the second light will turn green at $t +\tau$. Solve for $\tau = k\dfrac{T}{10}, k = 0,\cdots,9$. 
Plot your results of capacity vs $\tau$ and determine the optimal delay $\tau$.

## Solutions

{: .new-title}
> Question 1
>
> For both Roe's Scheme and Godunov's Scheme, look at the problem of a traffic light
turning green at time $t = 0$. We are interested in the solution at $t = 2$ using both schemes.
What do you observe for each of the schemes? Explain briefly why the behavior you get
arises.
> 
> Use the following problem parameters:
> 
> $$\begin{aligned}
\rho_{\max}&=1.0, & \rho_L&=0.8 \\
u_{\max}&=1.0,  \\
\Delta x&=\dfrac{4}{400}, & \Delta t&=\dfrac{0.8\Delta x}{u_{\max}}.
\end{aligned}$$
> 
> The initial condition at the instant when the traffic light turns green is
> 
> $$\rho(0)=\left\{\begin{aligned}
&\rho_L, &&x < 0, \\
&0, && x\ge 0.
\end{aligned}\right.$$
