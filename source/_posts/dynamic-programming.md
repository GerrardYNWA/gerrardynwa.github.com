title: 动态规划： DP一时爽，一直DP一直爽
date: 2019-03-19 16:48:59
categories: Algorithm

tags: [interview problems, dynamic programming]
---

　　最具挑战性的算法问题一般都会涉及到最优化，这类问题中我们得找到一个解能够最大化或最小化某个函数。旅行商问题是一个经典的最优化问题，该问题中我们需要寻找一个巡游，以最小的总费用遍历途中所有的顶点。针对此问题很容易提出许多求解旅行商问题的”算法“，他们会生成一些看起来似乎很合理的解，但是无法在任何情况下构造出费用最少的巡游。
　　用于最优化问题的算法需要证明这种算法永远能返回最好的解。贪心算法在每一步都会做出局部最优决策，这样通常很高效，但也经常不能保证全局最优性。穷举搜索算法会尝试所有可能性并选择出最好的解，这样必然能产生最优解，但通常会导致其在时间复杂度上的代价极其高昂。
　　动态规划结合了上述两种算法思想中最优秀的特质。它给了我们一种以定制方式设计算法的方案，能让我们一边去存储结果（避免了重复计算，从而带来了高效性），一边系统性地按一定次序去搜索所有可能性（从而确保了正确性）。通过对所有可能有用的决策存储它们会带来的结果，再以一种系统性的方式使用这类信息，最终让总计算量得到了最小化。
　　对于那些有着内蕴的的从左到右、从上到下次序的组合式对象（如字符串、有根树、多边形、整数序列等）的最优化问题，动态规划通常都是可考虑的求解方案。

<!--more-->

### 一、动态规划基础
　　动态规划本质上说是一种拿空间去换时间的策略。动态规划的第一种动机是利用递归的重叠子问题，进行记忆化求解，即先用递归法解决问题，再利用重叠子问题转化为动态规划。下面我们来看看计算斐波拉契数列的三种不同的方式。

1. 递推
2. 记忆化搜索
3. 最优化原理与最优子结构
4. 状态和状态转移方程
5. 无后效性
6. 决策和多阶段决策问题

　　动态规划的另一种动机即是多阶段决策思想。递归思想和多阶段决策思想是对称的：用递归思路建立模型，容易算出状态的前趋，适合顺推；用多阶段决策建立模型，容易算出状态的后继，适合逆推。


### 二、经典模型
1. 线性模型
2. 串模型
3. 区间模型
4. 背包模型
5. 状态压缩模型
6. 树状模型

### 三、常用状态转移方程
1. 方程一（1D/1D）
2. 方程二（2D/0D）
3. 方程三（2D/1D）
4. 方程四（2D/2D）

### 四、优化方法
1. 滚动数组
2. 最长单调子序列
3. 矩阵优化
4. 斜率优化
5. 树状数组优化
6. 线段优化
7. 散列Hash优化

### 五、经典题解