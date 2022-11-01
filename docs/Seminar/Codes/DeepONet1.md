---
layout: default
title: DeepONet
parent: 读懂代码系列
grand_parent: 讨论班
nav_order: 1
---

发布日期：2022年8月17日

{: .warning }
> 本页未完成.

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
        [m, 128, 128, 128, 128], [1, 128, 128, 128], "tanh", "Glorot normal"
    )
    net.apply_feature_transform(periodic)

    scaler = StandardScaler().fit(y_train)
    std = np.sqrt(scaler.var_.astype(np.float32))

    def output_transform(inputs, outputs):
        return outputs * std + scaler.mean_.astype(np.float32)

    net.apply_output_transform(output_transform)

    data = dde.data.TripleCartesianProd(x_train, y_train, x_test, y_test)
    model = dde.Model(data, net)

    lr = 0.001
    epochs = 500000
    train(model, lr, epochs)

```


