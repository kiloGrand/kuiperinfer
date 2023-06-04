# KuiperCourse

![KuiperInfer-logo](https://picx.zhimg.com/v2-ba937e1485bdd863a237b42bb1909e9f_1440w.jpg?source=172ae18b)

## 介绍
此GitHub项目是一个初学者的深度学习框架，使用C++编写，旨在为用户提供一种简单、易于理解的深度学习实现方式。以下是本项目的主要特点和功能：

* 计算图：使用计算图来描述深度学习模型的计算过程，利用计算图将神经网络的计算过程视为一个有向无环图。通过构建计算图，可以将深度学习模型转化为一系列的计算节点，通过节点之间的连接来表达模型的计算逻辑，使得计算过程可视化并易于维护和优化。

* 张量：使用Tensor类封装张量，支持float类型数据，并提供了访问张量属性和元素的接口以及一些查询、修改张量属性的函数。在计算图中，使用张量来表示各个操作的输入和输出，将神经网络中的所有数据表示为张量，以支持并行计算。

* 前向传播：实现了基础的前向传播。可以自定义神经网络结构，如添加层、激活函数等。

* 易于扩展：模块化设计使得用户可以轻松地添加新的模块或算法，以适应不同的任务需求。

通过学习和使用这个项目，用户可以深入了解计算图、张量、前向传播，使用C++构建简单的深度学习框架。
同时，本项目也为用户提供了一个基础框架，以便他们可以更全面地研究、开发和部署深度学习算法。


## 开发环境
- 系统：ubuntu 22.04
- 开发语言：C++ 17 
- 数学库：Armadillo + OpenBlas
- 加速库：OpenMP
- 单元测试：Google Test
- 性能测试：Google Benchmark
- 其他：opencv + glog


## 搭建环境

### 使用Linux对应发行版的包管理器安装必要的组件
- Fedora & Red Hat: cmake, openblas-devel, lapack-devel, arpack-devel, SuperLU-devel
- Ubuntu & Debian: cmake, libopenblas-dev, liblapack-dev, libarpack2-dev, libsuperlu-dev

Ubuntu: 
```bash
sudo apt update
sudo apt install cmake libopenblas-dev liblapack-dev libarpack2-dev libsuperlu-dev
```

### armadillo-11.4.2（背后调用OpenBlas）的编译安装
- 源码下载地址：https://arma.sourceforge.net/docs.html
- 安装：
```bash
mkdir build
cd build
cmake ..
make -j8
sudo make install
```

### Glog日志库和GTest测试库的编译安装
源码下载地址：
- https://github.com/google/googletest
- https://github.com/google/glog

先安装glog，再安装gtest，两者之间有依赖关系。
```bash
git clone https://github.com/google/glog.git
cd glog
mkdir build
cd build
cmake ..
make -j8
sudo make install
```

```bash
git clone https://github.com/google/googletest.git
cd googletest
mkdir build
cd build
cmake ..
make -j8
sudo make install
```

### Google Benchmark的编译安装
```bash
git clone https://github.com/google/benchmark.git
git clone https://github.com/google/googletest.git benchmark/googletest
cd benchmark
mkdir build && cd build
cmake ..
make -j2
sudo make install
```

### opencv的安装
```bash
sudo apt install libopencv-dev
```


## 本项目的编译
本项目是对b站上的课程[KuiperCourse第14次课程](https://www.bilibili.com/video/BV1xs4y1J7t2/)代码的解读，详细分析请看`tutorials`文件夹下的文件。

```bash
git clone https://github.com/zjhellofss/KuiperCourse.git
cd KuiperCourse
git checkout thirteen
mkdir build && cd build
cmake ..
make -j2
```

也可以使用Clion进行编译。


## 未来工作
1. 移植并实现任意一个深度学习模型，需要附加 demo 程序供演示。模型需要的 PNNX 文件获取方法，请自行参考 PNNX 项目
2. 优化任意一个或多个算子，使得运行速度在本机上加快 5%以上。时间测评以 Google Benchmark 框架为准，该框架使用方法请自行查阅。
3. 预研 Kuiperinfer 上的量化方法，并根据实际情况完成一个（含）以上算子的 int8 量化实现，推荐阅读资料 https://github.com/BUG1989/caffe-int8-convert-tools
4. 支持 Kuiperinfer 的Python API，推荐使用 Pybind 实现。
5. 优化 Kuiperinfer 的运行时需要的内存空间，使得总体资源消耗减少 5% 以上。推荐从算子输出空间复用着手（不同算子执行时空不同，它们的输出空间理论上可以复用）。
6. 预研 Kuiperinfer 上的算子并行方法（并行算子调度），并根据个人实际情况写出它的对应实现。


与作者进行交流：将整个项目的代码、实验报告、预研文档（如果有的话）打包发送到邮箱 hellofss@foxmail.com。

