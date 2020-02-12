title: 视觉SLAM十四讲——三维空间刚体运动
date: 2017-08-11 22:27:49
categories: Algorithm

tags: [computer vision, slam]
---

　　重新整理学习《视觉SLAM十四讲》：三维空间刚体运动
<!-- more -->

## 1. 向量和坐标系（参考系）

### 1.1 向量

　　向量是线性空间中的一个元素，可以把它想象成从原点指向某处的一个箭头。只有当我们指定三维空间的坐标系时，才可以讨论该向量在此坐标系下的坐标。如果我们确定了一个坐标系，也就是一个线性空间的基 $ (\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3)$，那么向量在这组基下的坐标为：
$$
\mathbf{a} = [\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3][a_1, a_2, a_3]^T = a_1 \mathbf{e}_1 + a_2 \mathbf{e}_2 + a_3 \mathbf{e}_3
$$

#### 点积（内积）

内积是一个标量，对应位一一相乘之后求和可得，可以描述向量间的投影关系。

#### 叉积（外积）

外积只对三维向量存在定义，外积的方向垂直于这两个向量，大小为这两个向量张成的面积。

### 1.2 坐标系

- 左手坐标系
- 右手坐标系

## 2. 旋转表示方式

### 2.1 旋转矩阵与欧氏变换

- 欧拉定理（Euler’s Rotation Theorem）:刚体在三维空间里的一般运动，可分解为刚体上方某一点的平移，以及绕经过此点的旋转轴的转动
- 齐次坐标与变换矩阵
- 旋转加平移在表达复合情况下有不便之处
- 齐次坐标乘任意非零常数时仍表达同一坐标
- 变换矩阵逆形式

### 2.2 旋转向量(轴角)

- 旋转矩阵R有九个元素，但仅有三个自由度
- 旋转向量与矩阵的不同（仅有三个量、无约束、更直观）
- 罗德里格斯公式（旋转向量->旋转矩）
- 旋转矩阵转旋转向量

### 2.3 欧拉角

- 将旋转分解为三个方向上的转动
- yaw-pitch-roll，东北天
- 万向锁（欧拉角的奇异性问题，欧拉角不适合插值或迭代）
- 仅用三个实数表达旋转时，不可避免地存在奇异性问题
- SLAM中很少用欧拉角表达姿态

### 2.4 四元数

- 2D情况，可用单位复数表达旋转
- 3D情况，四元数可作为复数的扩充
- 四元数到角轴（角轴到四元数）
- 如何用四元数旋转一个空间点
- 四元数相比角轴、欧拉角的优势（紧凑、无奇异性）

## 3. 面试题

### 1. 齐次坐标和非齐次坐标

### 2. 点的齐次坐标和向量齐次坐标的区别及应用

### 3. 说一下3D空间的位姿如何去表达?

### 4. 位姿不同表示间的相互转换、旋转矩阵特征值和特征向量物理意义

### 5. 相似变换、仿射变换、射影变换的区别及自由度


