---
title: 数据结构与算法随笔
categories: 随笔
tags: [随笔]
---
# Data Struture Note
<!-- TOC -->

- [1. 如何解决`hash`冲突，有哪几种方案](#1-如何解决hash冲突有哪几种方案)
    - [1.1. 开放定址法](#11-开放定址法)
    - [1.2. 链地址法（拉链法）](#12-链地址法拉链法)
    - [1.3. 再哈希法](#13-再哈希法)
    - [1.4. 建立公共溢出区](#14-建立公共溢出区)

<!-- /TOC -->
## 1. 如何解决`hash`冲突，有哪几种方案
参考：[解决哈希冲突的常用方法分析](https://www.jianshu.com/p/4d3cb99d7580)
### 1.1. 开放定址法
- 线性探查法：找到下一个有空的位置放进去，查找的时候遍历（其实也可以有一个辅助的数组专门记录移动的位置），这个方法容易出现“聚集”的现象
- 平方探查法：二次探测法的地址增量序列为 di = 12， -12， 22， -22，… ， q2, -q2 (q <= m/2)。二次探测能有效避免“聚集”现象，但是不能够探测到哈希表上所有的存储单元，但是至少能够探测到一半。若探查到一半单元仍找不到一个空闲单元，表明此散列表太满，应该重新建立。
- 双散列函数探查法： hp (key)若h(key)出现冲突，则再使用hp (key)求取散列地址。探查序列为：`h(k), h(k)+ hp(k),…, h((k)+ i*hp(k))`。

### 1.2. 链地址法（拉链法）
`Java`中`HashMap`的经典实现算法。

### 1.3. 再哈希法
当发生冲突时，使用第二个、第三个、哈希函数计算地址，直到无冲突时。缺点：计算时间增加。
### 1.4. 建立公共溢出区
将哈希表分为公共表和溢出表，当溢出发生时，将所有溢出数据统一放到溢出区。