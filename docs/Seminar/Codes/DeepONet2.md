---
layout: default
title: DeepONet(续)数据存储
parent: 读懂代码系列
grand_parent: 讨论班
nav_order: 2
---

发布日期：2022年11月5日

{: .new }
> TODO: 搞懂把$u$变成features的存储方法.


参考文献: 
- Lu, L. et al, (2019), ‘DeepONet: Learning nonlinear operators for identifying differential equations based on the universal approximation theorem of operators’, arXiv preprint arXiv:1910.03193


本文主要目的是搞懂这篇文章在ODE情形的`gen_operator_data`方法. 


```python
from __future__ import absolute_import
from __future__ import division
from __future__ import print_function

import itertools

import numpy as np
import tensorflow as tf

import deepxde as dde
from spaces import FinitePowerSeries, FiniteChebyshev, GRF
from system import LTSystem, ODESystem, DRSystem, CVCSystem, ADVDSystem
from utils import merge_values, trim_to_65535, mean_squared_error_outlier, safe_test


def ode_system(T):
    """ODE"""

    def g(s, u, x):
        # Antiderivative
        return u
        # Nonlinear ODE
        # return -s**2 + u
        # Gravity pendulum
        # k = 1
        # return [s[1], - k * np.sin(s[0]) + u]

    s0 = [0]
    # s0 = [0, 0]  # Gravity pendulum
    return ODESystem(g, s0, T)

```

    输出：C:\Users\Fiddie\AppData\Local\Programs\Python\Python310\lib\site-packages\numpy\_distributor_init.py:30: UserWarning: loaded more than 1 DLL from .libs:
    C:\Users\Fiddie\AppData\Local\Programs\Python\Python310\lib\site-packages\numpy\.libs\libopenblas.EL2C6PLE4ZYW3ECEVIV3OXXGRN2NRFM2.gfortran-win_amd64.dll
    C:\Users\Fiddie\AppData\Local\Programs\Python\Python310\lib\site-packages\numpy\.libs\libopenblas.FB5AE2TYXYH2IJRDKGDGQ3XBKLKTF43H.gfortran-win_amd64.dll
      warnings.warn("loaded more than 1 DLL from .libs:"
    Using backend: tensorflow.compat.v1
    
    

    WARNING:tensorflow:From C:\Users\Fiddie\AppData\Local\Programs\Python\Python310\lib\site-packages\tensorflow\python\compat\v2_compat.py:107: disable_resource_variables (from tensorflow.python.ops.variable_scope) is deprecated and will be removed in a future version.
    Instructions for updating:
    non-resource variables are not supported in the long term
    WARNING:tensorflow:From C:\Users\Fiddie\AppData\Local\Programs\Python\Python310\lib\site-packages\deepxde\nn\initializers.py:118: The name tf.keras.initializers.he_normal is deprecated. Please use tf.compat.v1.keras.initializers.he_normal instead.
    
    


```python
T = 1
m = 100
num_train = 200
space = GRF(1, length_scale=0.2, N=1000, interp="cubic")
system = ode_system(T)
X_train, y_train = system.gen_operator_data(space, m, num_train)
print(type(X_train), type(y_train))
```

    输出：Generating operator data...
    'gen_operator_data' took 3.986554 s
    
    <class 'list'> <class 'numpy.ndarray'>
    


```python
print(X_train)
```

    输出：[array([[-0.94639949, -0.97406677, -1.00125566, ..., -0.14449401,
            -0.09228728, -0.03347635],
           [-2.92668791, -2.901142  , -2.86283726, ..., -0.3182825 ,
            -0.29599596, -0.27562289],
           [ 0.81009706,  0.80270408,  0.79311753, ...,  0.57981669,
             0.58427741,  0.59365942],
           ...,
           [-0.17947488, -0.16850695, -0.15723532, ..., -0.18693907,
            -0.170121  , -0.15240866],
           [-0.96752331, -1.04870691, -1.13172916, ...,  0.87918971,
             0.92470479,  0.96921787],
           [-0.63096154, -0.60280519, -0.56714925, ...,  1.41298683,
             1.46618776,  1.51727376]]), array([[0.96025645],
           [0.46332248],
           [0.71957716],
           [0.39823714], 
               ...
           [0.09492193],
           [0.95758642],
           [0.78606259]])]
    


```python
X_train[0] #sensor values
```




    输出：array([[-0.94639949, -0.97406677, -1.00125566, ..., -0.14449401,
            -0.09228728, -0.03347635],
           [-2.92668791, -2.901142  , -2.86283726, ..., -0.3182825 ,
            -0.29599596, -0.27562289],
           [ 0.81009706,  0.80270408,  0.79311753, ...,  0.57981669,
             0.58427741,  0.59365942],
           ...,
           [-0.17947488, -0.16850695, -0.15723532, ..., -0.18693907,
            -0.170121  , -0.15240866],
           [-0.96752331, -1.04870691, -1.13172916, ...,  0.87918971,
             0.92470479,  0.96921787],
           [-0.63096154, -0.60280519, -0.56714925, ...,  1.41298683,
             1.46618776,  1.51727376]])




```python
X_train[0].shape #200个100维数组
```




    输出：(200, 100)




```python
X_train[1] #x values
```




    输出：array([[0.96025645],
           [0.46332248],
           [0.71957716],
               ...
           [0.09492193],
           [0.95758642],
           [0.78606259]])




```python
X_train[1].shape
```




    输出：(200, 1)




```python
y_train.shape
```




    输出：(200, 1)



关于`gen_operator_data`的一些细节解释：

```python
def eval_s_space(self, space, features, x):
    """For a list of functions in `space` represented by `features`
    and a list `x`, compute the corresponding list of outputs.
    """

    def f(feature, xi):
        return self.eval_s(lambda t: space.eval_u_one(feature, t), xi[0])
    #space.eval_u_one(feature, t)的作用：把(feature, t)变成u(t)

    p = ProcessPool(nodes=config.processes)
    res = p.map(f, features, x)
    return np.array(list(res))

def eval_s_func(self, u, x):
    """For an input function `u` and a list `x`, compute the corresponding list of outputs.
    """
    res = map(lambda xi: self.eval_s(u, xi[0]), x)
    return np.array(list(res))

def eval_s(self, u, tf):
    def f(t, y):
        return self.g(y, u(t), t)
    sol = solve_ivp(f, [0, tf], self.s0, method="RK45")
    return sol.y[0, -1:]
```

我们求解的问题是

$$\dfrac{\mathrm{d}y}{\mathrm{d}t}=f(t,y)=g(y,u(t),t), \qquad (*)$$

初值条件是$y(0)=s_0$, 区间为$[0,tf]$.

```python
def gen_operator_data(self, space, m, num):
    print("Generating operator data...", flush=True)
    features = space.random(num)
    sensors = np.linspace(0, self.T, num=m)[:, None] 
    sensor_values = space.eval_u(features, sensors)
    x = self.T * np.random.rand(num)[:, None]
    y = self.eval_s_space(space, features, x)
    return [sensor_values, x], y
```

返回的值是`[sensor_values, x], y`, 于是`X_train[0]`就是`sensor_values`, `X_train[1]`就是`x`, `y_train`就是`y`.

`sensor_values`存放的是问题$(*)$的解的一些离散点(在某些$x$处的点)


```python
sensors = np.linspace(0, T, num=m)[:, None] 
sensors.shape
```




    输出：(100, 1)



`sensors`是$m=100$维数组. 

`sensor_values`是在`sensors`处的函数值(计算$num=200$个不同的features, 得到对应的函数值)

`features`实际上存放的是不同的$u$(见一开始的代码)，但是需要作一个feature-wise transformation. 对于不同的$u$(即不同的features), 我们会得到不同的函数. 而这些函数的数据在`sensor_values`中存储. 

论文原文：Finding an effective way to represent the conditioning input and merge the embeddings is still an open question, and different approaches have been proposed, such as feature-wise transformations

参考文献：Dumoulin, V. et al. Feature-wise transformations. Distill https://distill.pub/2018/feature-wise-transformations (2018).

