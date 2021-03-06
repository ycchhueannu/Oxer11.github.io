---
title: Graph Decompositions
toc: true
date: 2019-01-20 09:13:04
tags: [Graph Theory]
categories: 
- Graph Theory
- Chapter 02  Subgraphs
mathjax: true
---

图的分解(decomposition)是图论中基础的研究课题。本文将简介图分解的基本概念和与图分解相关的几个定理。

------

## 定义

> 给定图 $G$，若集合族 $\mathcal{F}$ 中的集合是图 $G$ 的**边不相交**的子图，且满足 $\cup_{F \in \mathcal{F}} E(F) = E(G)$，则称集合族 $\mathcal{F}$ 为图 $G$ 的一个分解。
> 
> 特别地，若 $\mathcal{F}$ 中的集合是由图 $G$ 中的路径构成的，则称 $\mathcal{F}$ 为图 $G$ 的路径分解(path decomposition)。若 $\mathcal{F}$ 中的集合是由图 $G$ 中的回路构成的，则称 $\mathcal{F}$ 为图 $G$ 的回路分解(cycle decomposition)。

------

## Veblen定理


显然，所有的图都有一个平凡的路径分解——分解为长度为 $1$ 的路径，而并不是所有的图都有一个回路分解。关于回路分解，有以下著名定理：


### 定理 2.7  Veblen's Theorem

> **定义：** 若无向图 $G$ 中所有节点度数都是偶数，则称无向图 $G$ 是偶图。
> 无向图 $G$ 有一个回路分解当且仅当它是偶图。

**证明：** 必要性。回路分解中的每条回路使该回路上的所有节点度数加二，因此图中每个节点的度数为它所在的回路个数 $\times 2$ 。故所有节点的度数均为偶数。

充分性。对图的边数进行归纳。

当图中边数为 $0$ 时，结论显然成立。

若图中边数不为 $0$，则只需考虑图中度数不为 $0$ 的节点。因为这些节点的度数至少为 $2$，所以图中至少存在一条回路 $C$ 。将该回路从边集中去掉后得到图 $G'$，节点度数的奇偶性不变，图中边数减少。由归纳假设，$G'$ 有一个回路分解 $\mathcal{F'}$，则 $\mathcal{F} = \mathcal{F'} \cup {C}$ 是图 $G$ 的一个回路分解。


### 练习 2.4.2 Veblen's Theorem (Digraph Version)

> **定义：** 若有向图 $G$ 中所有节点的入度都等于出度，则称有向图 $G$ 是偶图。
> 有向图 $G$ 有一个回路分解当且仅当它是偶图。

**证明：** 证明过程同定理 2.7，只需将度数为偶数的条件改为出度入度相等。

------

## 其它图分解

在组合问题的证明中引入的代数技巧，往往有奇效。下面的定理是由Graham和Pollak于1971年提出的，给出了完全图的完全二分图分解中，完全二分图的数量下界。Tverberg(1982)借助线性无关(linear independence)的技巧巧妙地证明了该定理。

### 定理 2.8

> 若 $\mathcal{F} : = \{F_1,F_2,...,F_k\}$ 是完全图 $K_n$ 的一个完全二分图分解。那么， $k \ge n-1$

**证明：** 令 $V$ 表示 $K_n$ 的顶点集，完全二分图 $F_i$ 的二划分记作 $(X_i,Y_i)$，$1 \le i \le k$ 。考虑下面 $k+1$ 个线性方程：

$$
\sum_{v \in V} x_v = 0，\quad \sum_{v \in X_i} x_v = 0 (1\le i \le k)
$$

若 $k < n-1$，则该方程组有 $n$ 个变量，不超过 $n-1$ 个方程，因此必有非零解。记方程组的非零解为 $x_v=c_v,v \in V$，其中至少存在一个 $c_v \neq 0$ 。

因为 $\mathcal{F}$ 是完全图 $K_n$ 的一个分解，所以
$$
\sum_{(v,w)\in E} c_v c_w = \sum_{i=1}^{k} \left(\sum_{v \in X_i} c_v\right)\left(\sum_{v \in Y_i} c_w\right)
$$

因此，
$$
0 = \left(\sum_{v \in V} c_v \right)^2 = \sum_{v \in V} c_v^2 + 2\sum_{i=1}^k \left(\sum_{v \in X_i} c_v\right)\left(\sum_{v \in Y_i} c_w\right) = \sum_{v \in V} c_v^2 > 0
$$
矛盾。所以， $k \ge n-1$ 

显然，定理 2.8中给出的下界是紧的，因为任意完全图 $K_n$ 可被分解为 $K_{1,k}$， $1\le k \le n-1$ 。


### 练习 2.4.7

> 若无向图 $G$ 是连通图，且有偶数条边
> a) 试证明可对图 $G$ 中每条边定向，使得每个节点的出度为偶数。

**证明：** 先对图 $G$ 任意定向，通过调整使得所有节点出度为偶数。

若图 $G$ 中所有节点出度都为偶数，则无需调整。

若图 $G$ 中存在节点 $u$ 的出度是奇数，因为图 $G$ 中有偶数条边，而所有节点的出度之和等于边数，所以必存在另一节点 $v$ 的出度也是奇数。因为无向图 $G$ 是连通的，可取图中 $u$ 到 $v$ 的一条路径 $P$，将路径 $P$ 上的边全部反向。对于节点 $u$ 和 $v$，恰好有一条与其相连的边改变方向，所以出度的奇偶性改变，均变为偶数。对于路径上其他的节点，因为有两条与其相连的边同时改变方向，所以出度的奇偶性不变，仍为偶数。
持续做如上调整，直至图中所有节点都为偶数。

因此，存在一种定向方式，使得每个节点的出度均为偶数。


> b) 试证明图 $G$ 有一个路径分解，其中每条路径长度都为 $2$

**证明：** 因为图 $G$ 可定向为出度均为偶数的有向图。对于节点 $u$，取其在有向图中指向的两个节点 $v,w$，则路径 $v,u,w$ 是原图 $G$ 中长度为 $2$ 的一条路径。因为在定向后的有向图中所有节点的出度均为偶数，所以可持续该过程，直至所有边都被覆盖。此时，将得到一个原图 $G$ 的长度为 $2$ 的路径分解。


### 练习 2.4.8

> 每个无自环的有向图都可分解为两个无环有向图。

**证明：** 记有向图 $G$ 中节点为 $v_1,v_2,...,v_n$。全序集 $v_1 \le v_2 \le ... \le v_n$ 对应的竞赛图记为 $F'$，全序集 $v_n \le v_{n-1} \le ... \le v_1$ 对应的竞赛图记为 $F''$ 。由全序集的传递性可知，图 $F'$ 和 $F''$ 是无环的。原图 $G$ 中的每条边要么属于 $F'$，要么属于 $F''$，所以 $\mathcal{F} = \{E(F') \cap E(G), E(F'') \cap E(G)\}$ 恰好构成图 $G$ 的一个无环有向图分解。

------

## 参考资料
> - Bondy, John Adrian, and Uppaluri Siva Ramachandra Murty. *Graph theory with applications*. Vol. 290. London: Macmillan, 1976.
