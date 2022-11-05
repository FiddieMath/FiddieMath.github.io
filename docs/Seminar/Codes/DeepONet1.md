---
layout: default
title: DeepONet
parent: 读懂代码系列
grand_parent: 讨论班
nav_order: 1
---

发布日期：2022年11月4日

{: .warning }
> 本页未完成.

{: .new }
> TODO: 不能每次得到神经网络的隐藏参数都要跑一遍程序, 后面需要研究一下如何把神经网络的隐藏参数保存到本地, 方便后续调用.

{: .no_toc }

<details open markdown="block">
  <summary>
    目录
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

参考文献: 
- Lu, L. et al, (2019), ‘DeepONet: Learning nonlinear operators for identifying differential equations based on the universal approximation theorem of operators’, arXiv preprint arXiv:1910.03193
- L. Lu, X. Meng, Z. Mao, and G. E. Karniadakis. DeepXDE: A deep learning library for solving differential equations. arXiv preprint arXiv:1907.04502, 2019.
- L. Lu, X. Meng, S. Cai, Z. Mao, S. Goswami, Z. Zhang, & G. E. Karniadakis. A comprehensive and fair comparison of two neural operators (with practical extensions) based on FAIR data. Computer Methods in Applied Mechanics and Engineering, 393, 114778, 2022.

DeepONet链接：https://github.com/lululxvi/deeponet

DeepONet需要用到DeepXDE, 但是DeepXDE也在不断更新, 所以上面这个DeepONet版本比较旧了, 有些地方是跑不动的.
采用最新的DeepXDE的DeepONet代码链接为: 

[https://github.com/lu-group/deeponet-fno](https://github.com/lu-group/deeponet-fno)



# 安装

在使用DeepONet之前，需要安装DeepXDE，链接：[https://github.com/lululxvi/deepxde](https://github.com/lululxvi/deepxde)

安装方法: 在控制台中输入

```python
pip install deepxde
```

其他需要的包为: 
- matplotlib
- numpy
- pathos
- scipy
- sklearn
- tensorflow
- tensorflow_addons
- torch

需要下载作者提供的数据集(放在了OneDrive云盘)才能跑作者提供的算例. 

# 运行

安装完所需的包以后, 我们尝试运行一下. 在控制台运行`src/burgers/deeponet.py`即可进行训练. 
我们下面详细介绍这个文件的各个组成部分.

```python

def main():
    x_train, y_train, x_test, y_test = get_data(1000, 200)

    m = 2 ** 7
    net = dde.maps.DeepONetCartesianProd(
        [m, 128, 128, 128, 128],  #layer_sizes_branch
        [1, 128, 128, 128],       #layer_sizes_trunk
        "tanh",                   #activation function
        "Glorot normal"           #Kernel initializer
    )
```

定义一个DeepONet. 四个参数分别表示初始化branch net的大小、trunk net的大小、激活函数、初始化神经网络采取的分布.
可参见`deepxde\nn\tensorflow`.

```python
    net.apply_feature_transform(periodic)

    scaler = StandardScaler().fit(y_train)
    std = np.sqrt(scaler.var_.astype(np.float32))

    def output_transform(inputs, outputs):
        return outputs * std + scaler.mean_.astype(np.float32)
        
    net.apply_output_transform(output_transform)
```

`apply_feature_transform`的作用是对神经网络的输入作用一个变换, 得到features. 
用法：`features = transform(inputs)`. 然后, `outputs = network(features)`.

这些代码的作用应该是对初始化的参数做归一化处理.


这里的periodic返回`[cos(2pi*x), sin(2pi*x), cos(4pi*x), math.sin(4pi*x)], 1`, 
表示我们考虑做Fourier展开然后取Fourier系数? (还得细看, 不太清楚)

```python
    data = dde.data.TripleCartesianProd(x_train, y_train, x_test, y_test)
    model = dde.Model(data, net)

    lr = 0.001            #学习率
    epochs = 500000       #迭代次数
    train(model, lr, epochs)
```

`dde.Model`在`deepxde\model.py`中.

```python
def train(model, lr, epochs):
    decay = ("inverse time", epochs // 5, 0.5)
    model.compile("adam", lr=lr, metrics=["mean l2 relative error"], decay=decay)
    losshistory, train_state = model.train(epochs=epochs, batch_size=None)
    # dde.postprocessing.save_loss_history(losshistory, "loss.dat") 
    print("\nTraining done ...\n")
```

## 数据提供

`main()`的一开始提供了数据集:

```python
x_train, y_train, x_test, y_test = get_data(1000, 200)
```

`get_data()`的具体代码如下：

```python
def get_data(ntrain, ntest):
    sub_x = 2 ** 6
    sub_y = 2 ** 6

    # Data is of the shape (number of samples = 2048, grid size = 2^13)
    data = io.loadmat("burgers_data_R10.mat")
    x_data = data["a"][:, ::sub_x].astype(np.float32)
    y_data = data["u"][:, ::sub_y].astype(np.float32)
    x_branch_train = x_data[:ntrain, :]
    y_train = y_data[:ntrain, :]
    x_branch_test = x_data[-ntest:, :]
    y_test = y_data[-ntest:, :]

    s = 2 ** 13 // sub_y  # total grid size divided by the subsampling rate
    grid = np.linspace(0, 1, num=2 ** 13)[::sub_y, None]

    x_train = (x_branch_train, grid)
    x_test = (x_branch_test, grid)
    return x_train, y_train, x_test, y_test
```

需要用户自己提供数据集(存放在Matlab的mat文件中), 这个文件大小是600多M. 对于一些复杂的问题, 我们需要手动去用现有的模拟软件去求近似解来作为数据集,
并且还要清楚数据集的存放方式(数据结构).
<div align = center>
<img src="/pics/DeepONetpy1.png" width = "300"/>
</div>


## DeepXDE中对DeepONet的定义

DeepONet网络结构的定义位于`deepxde\nn\tensorflow\deeponet.py`, 存放在`DeepONetCartesianProd`类里面. 其初始化的代码如下:

```python
    if callable(layer_sizes_branch[1]):
        # User-defined network
        self.branch = layer_sizes_branch[1] 
    else:
        # Fully connected network
        self.branch = FNN(
            layer_sizes_branch,
            activation_branch,
            kernel_initializer,
            regularization=regularization,
        )
    self.trunk = FNN(
        layer_sizes_trunk,
        self.activation_trunk,
        kernel_initializer,
        regularization=regularization,
    )
    self.b = tf.Variable(tf.zeros(1, dtype=config.real(tf)))
```

这里给用户提供了一个branch net的自行定义方式, 默认的定义方式是一个全连接神经网络.
另外trunk net默认是一个神经网络. 此外要训练的参数还有一个常数b.

为了从DeepONet中得到返回值(或者函数值), 需要定义一个`call`方法:

```python
#inputs: 一个二元组包括x_func和x_loc(计算函数x_func在x_loc处的值)

def call(self, inputs, training=False): 
    x_func = inputs[0] #这里的x_func应该已经变成一个数组(离散点)的形式了.
    x_loc = inputs[1]  
    
    x_func = self.branch(x_func) #把x_func输入到branch net, 输出值仍存储到x_func
    
    if self._input_transform is not None: 
        x_loc = self._input_transform(x_loc) 
    x_loc = self.activation_trunk(self.trunk(x_loc)) #把x_loc输入到branch_net，输出值仍存储到x_loc
    
    if x_func.shape[-1] != x_loc.shape[-1]:
        raise AssertionError(
            "Output sizes of branch net and trunk net do not match."
        )
    x = tf.einsum("bi,ni->bn", x_func, x_loc) #计算x_func · x_loc （点乘）的结果
    
    x += self.b  #增加bias

    if self._output_transform is not None:
        x = self._output_transform(inputs, x)
```

## DeepXDE中对Model类的定义

### 初始化

```python
def __init__(self, data, net):
    self.data = data   # 用户提供训练的数据
    self.net = net     # 用户提供神经网络的模型
## ……（不太重要的东西）
```

### `compile`方法

```python
def compile(
    self,
    optimizer,     #优化器(string类型)
    lr=None,       #学习率(如果用L-BFGS, 需要用``dde.optimizers.set_LBFGS_options``方法来定义多个参数)
    loss="MSE",    #损失函数默认为MSE
    metrics=None,  
    decay=None,    #学习率的衰减速度
    loss_weights=None, #损失函数的权重系数
    external_trainable_variables=None, #其他要训练的变量
):
    print("Compiling model...")
    self.opt_name = optimizer
    loss_fn = losses_module.get(loss)  #损失函数
    self.losshistory.set_loss_weights(loss_weights)
    if external_trainable_variables is None:
        self.external_trainable_variables = []
    else:
        if backend_name == "tensorflow.compat.v1":
            print(
                "Warning: For the backend tensorflow.compat.v1, "
                "`external_trainable_variables` is ignored, and all trainable "
                "``tf.Variable`` objects are automatically collected."
            )
        if not isinstance(external_trainable_variables, list):
            external_trainable_variables = [external_trainable_variables]
        self.external_trainable_variables = external_trainable_variables

    if backend_name == "tensorflow.compat.v1":
        self._compile_tensorflow_compat_v1(lr, loss_fn, decay, loss_weights)
    elif backend_name == "tensorflow":
        self._compile_tensorflow(lr, loss_fn, decay, loss_weights)
    elif backend_name == "pytorch":
        self._compile_pytorch(lr, loss_fn, decay, loss_weights)
    elif backend_name == "jax":
        self._compile_jax(lr, loss_fn, decay, loss_weights)
    elif backend_name == "paddle":
        self._compile_paddle(lr, loss_fn, decay, loss_weights)
    # metrics may use model variables such as self.net, and thus are instantiated
    # after backend compile.
    metrics = metrics or []
    self.metrics = [metrics_module.get(m) for m in metrics]
```