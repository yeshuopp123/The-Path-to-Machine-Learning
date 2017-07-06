---
title: Tensorflow学习：常用API
date: 2017-07-06 16:18:40
tags:
---

+ [tf.Variable()](https://www.tensorflow.org/api_docs/python/tf/Variable)

# 常用Math操作
## [tf.random_normal()](https://www.tensorflow.org/api_docs/python/tf/random_normal)

### 作用

输出满足正态分布的随机值

### 说明
```
random_normal(
    shape,
    mean=0.0,
    stddev=1.0,
    dtype=tf.float32,
    seed=None,
    name=None
)
```
+ shape:一维整数张量/python数组，表示输出的张量的形状。
+ mean：类型为dtype的零维张量/python值。平均值。
+ stddev：类型为dtype的零维张量/python值。标准差。
+ dtype：输出数据的类型。
+ seed：用于作为生成随机数的种子。
+ name：为操作起个名字（可选）

## [tf.zeros()](https://www.tensorflow.org/api_docs/python/tf/zeros)

### 作用
创建一个所有元素都为零的张量。

### 说明
```
zeros(
    shape,
    dtype=tf.float32,
    name=None
)
```
+ shape: 一维整数张量/python数组
+ name: 为操作起个名字（可选）
+ dtype: 输出数据的类型

## [tf.global_variables_initializer()](https://www.tensorflow.org/api_docs/python/tf/global_variables_initializer)

### 作用
返回一个初始化全局变量的操作（op）
是variable_initializer(global_variables())的缩写。

## [tf.square](https://www.tensorflow.org/api_docs/python/tf/square)
### 作用
计算平方
### 说明
```
square(
    x,
    name=None
)
```
## [tf.reduce_mean](https://www.tensorflow.org/api_docs/python/tf/reduce_mean)

### 作用
计算张量某一维度上的平均值
### 说明
```
reduce_mean(
    input_tensor,
    axis=None,
    keep_dims=False,
    name=None,
    reduction_indices=None
)
```
+ input_tensor:输入一个张量
+ axis:指定某一个维度。比如test = [[[1.0,2],[3,4]],[[5,6],[6,7]]]，则可选值为0，1，2
+ keep_dims：输出是否保持原来的维度。
+ name：给操作起个名字
+ reduction_indices：axis的旧名字，不赞成用，可忽略。

# 常用Optimizer类
## [tf.train.GradientDescentOptimizer()](https://www.tensorflow.org/api_docs/python/tf/train/GradientDescentOptimizer)

learning_rate: A Tensor or a floating point value. The learning rate to use.
use_locking: If True use locks for update operations.
name: Optional name prefix for the operations created when applying gradients. Defaults to "GradientDescent".
