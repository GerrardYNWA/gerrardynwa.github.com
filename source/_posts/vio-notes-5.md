title: VIO课程笔记（第5讲）
date: 2019-07-16 21:25:19
categories: Algorithm

tags: [computer vision, slam, vio]
---
　　[深蓝学院《从零开始手写VIO》](http://www.shenlanxueyuan.com/course/160)课程笔记——第5讲：滑动窗口算法实践
<!-- more -->

## Section 1 - 非线性最小二乘问题求解

### 1. 非线性最小二乘问题求解：solver

- 高斯牛顿求解流程
  - 对应的高斯牛顿求解，normal equation：Hx = -b
  - 连加形式：信息矩阵
  - 直接求解$ \Delta x = - H^{-1}b $，计算量大
- 利用 舒尔补加速SLAM问题的求解
  - 舒尔补：利用SLAM问题的稀疏性求解

### 2. solver全流程回顾

- Cspare、CHOLMOD、PCG？

### 3. solver求解中的小疑问

- 信息矩阵H不满秩，那求解的时候如何操作？

  1. 使用LM算法，加阻尼因子使得系统满秩，可求解 ，但是 求得的结果可能会往零空间变化。
  2. 添加先验约束，增加系统的可观性。比如g2o tutorial中对第一个pose的信息矩阵加上单位阵$ H_{[11]} += I $。
  3. orbslam、svo等等求mono BA问题时，fix一个相机pose和一个特征点，或者fix两个相机pose，也是为了限定优化值不乱飘。那代码如何实现fix呢？
     - 添加超强先验，使得对应的信息矩阵巨大（如，$ 10^{15} $），就能使得$ \Delta x = 0 $；
     - 设定对应雅可比矩阵为0，意味着残差等于0。求解方程为$ (0 + \lambda I) \Delta x = 0 $，只能$ \Delta x = 0 $。

  ### 4. 单目Bundle Adjustment求解代码讲解

  - 核心问题：矩阵块的对应关系，如何拼接信息矩阵？

  ### 5. 单目Bundle Adjustment求解代码讲解

  - 顶点（vertex）
    - 变量加法运算
  - 边（edge）
    - 残差计算
    - 雅可比矩阵计算
    - 保存对应的顶点
  - 求解器（solver）
    - LM算法
    - 构建H、b
    - 线性求解器：QR、SVD、PCG...

## Section 2 - 滑动窗口算法

### 1. 滑动窗口算法回顾

### 2. 滑动窗口算法关键步骤可视化

- 步骤1：构建先验
- 步骤2：先验 + 新测量信息 —> 新的信息矩阵
- 和直接Bundle Adjustment相比，多了一个先验矩阵的维护

### 3. 滑动窗口算法中关键问题 

- 如何更新先验残差？
  - 目的：虽然先验信息矩阵固定不变，但随着迭代的推进，变量被不断优化，先验残差需要跟随变化。否则，求解系统可能崩溃。
  - 方法：先验残差的变化可以使用一阶泰勒展开

### 4. VINS-Mono中的滑动窗口算法

- two way marginalization
  - 当滑动窗口中第二新的图像帧为关键帧，则marg最老的帧，以及上面的路标点。
  - 当滑动窗口中第二新的图像帧，则丢弃这一帧上的视觉测量信息，IMU预积分传给下一帧。