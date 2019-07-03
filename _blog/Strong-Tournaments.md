---
title: Strong Tournaments
toc: true
date: 2019-01-19 14:43:19
tags: [Graph Theory]
categories: 
- Graph Theory
- Chapter 02  Subgraphs
mathjax: true
---

接上一篇文章，本文主要探究强连通的竞赛图有哪些特别的性质。

------

由上篇博文中的定理4可知，任意竞赛图都是半哈密尔顿图。而加上强连通的性质后，将得到更强的结论，下面的定理说明了，任意强连通的竞赛图都是哈密尔顿图。

### 定理 7

> 如果竞赛图 $\mathcal{T}$ 是强连通的，那么其中必存在长度为 $k = 3,4,...,n$ 的回路。

**证明：** 对回路长度进行归纳。

当 $k = 3$ 时，取 $\mathcal{T}$ 中任意节点 $x$ 。记 $x$ 指向的节点集合为 $U$，指向 $x$ 的节点集合为 $V$，因为 $\mathcal{T}$ 是强连通的，所以 $U,V$ 非空，且存在边 $(u,v),u\in U,V\in V$ 。因此，回路 $x,u,v,x$ 即为所求。

假设图中存在一条长度为 $k$ 的回路 $v_1,v_2,...,v_k,v_{k+1}=v_1$，下证明存在一条长度为 $k+1$ 的回路。

Case 1：若图中存在节点 $x$ 满足：存在边 $(v_i,x),(x,v_{i+1})$，则回路 $v_1,v_2,...v_i,x,v_{i+1},...,v_k,v_{k+1}=v_1$

Case 2：若图中无节点满足 Case 1 条件，则图中节点要么指向回路上所有点，要么被回路上所有店指向。因此，记被回路上所有点指向的点组成的集合为 $U$，指向回路上所有点的点组成的集合为 $V$，因为 $\mathcal{T}$ 是强连通的，所以 $U,V$ 非空，且存在边 $(u,v),u\in U,V\in V$ 。因此，回路 $v_1,u,v,v_3,...,v_k,v_{k+1}=v_1$ 即为所求。


由定理 7可以显然得到如下推论：


### 推论 7a

> 一个竞赛图是强连通的，当且仅当存在一条哈密尔顿回路。

------

## 环三元组

强连通的竞赛图必然不满足传递性，下面的推论给出了环三元组数量的下界。


### 推论 7b

> 若竞赛图 $\mathcal{T}$ 是强连通的，则其中至少包含 $n-2$ 个环三元组。

**证明：** 对图中节点个数进行归纳。

当 $n=3$ 时，结论显然成立。

假设对于任意 $n-1$ 个节点的强连通竞赛图，结论成立。下证明对于任意 $n$ 个节点的强连通竞赛图，其中至少包含 $n-2$ 个环三元组。

由定理 7，图中必存在长度为 $n-1$ 的回路$v_1,v_2,...,v_{n-1},v_n = v_1$，这 $n-1$ 个节点构成一个强连通的子竞赛图，其中包含 $n-3$ 个环三元组。记图中不在回路上的节点为 $x$，由图的强连通性可知，回路上存在连入 $x$ 的边，也存在 $x$ 连出的边。因此，存在正整数 $i < n$，使图中有边 $(v_i,x),(x,v_{i+1})$，这与边 $(v_i,v_{i+1})$ 构成新的环三元组。由此可知，结论成立。


通过构造，可以证明推论 7b中给出的下界是紧的。


### 推论 7c

> 存在 $n$ 个节点的强连通竞赛图，其中恰好包含 $n-2$ 个环三元组。

**证明：** 

对于 $n$ 个节点的满足传递性的竞赛图，其中的环三元组个数为 $0$。记图中入度为 $0$ 的点记为 $u$，出度为 $0$ 的点记为 $v$，将边 $(u,v)$ 反向，则新得到的图中恰好包含 $n-2$ 个环三元组。

对于图中除 $u,v$ 之外的任意节点 $x$，新图中 $u,v,x$ 恰好形成一个新的环三元组，这样的三元组共 $n-2$ 个。

原图中不包含节点 $u,v$ 的三元组必是传递三元组，而在新图中其仍保持传递性。

因此，由此方法构造的竞赛图恰好包含 $n-2$ 个环三元组。


上面的定理给出了环三元组数量对强连通竞赛图的必要条件，下面的定理将给出充分条件：


### 定理 8

> 若 $n$ 个节点的竞赛图 $\mathcal{T}$ 中环三元组的数量，比任意 $n-1$ 个节点的竞赛图都多，那么图 $\mathcal{T}$ 是强连通的。

**证明：** 记 $\mathcal{T}$ 中环三元组的个数为 $c$，由题意可知， $c > c_{max}(n-1)$

假设图 $\mathcal{T}$ 不是强连通的，则设其中包含至少 $2$ 个强连通分量，记这两个强连通分量的大小为 $k$ 与 $n-k$ 。由推论 5b，$\mathcal{T}$ 中的环三元组必然只出现在强连通分量内部，因此有 
$$
c \le c_{max}(k)+c_{max}(n-k) \le c_{max}(n-1)
$$
这与 $c > c_{max}(n-1)$ 矛盾，故 $\mathcal{T}$ 是强连通图。


由定理 8 可得下面的推论，其在判断竞赛图的连通性问题上有重要意义。


### 推论 8a

> 如果竞赛图中有 $n$ 个节点和 $c_{max}(n)$ 个环三元组，则该图是强连通的。

------

## 得分序列

加上强连通的性质后，竞赛图的得分序列也会产生相应的变化。

### 定理 9

> 若竞赛图 $\mathcal{T}$ 的得分序列为 $s_1\le s_2\le \cdots \le s_n$，那么 $\mathcal{T}$ 是强连通的，当且仅当下列方程成立：
> $$
> \sum_{i=1}^{n} s_i = \frac{1}{2} n (n-1) \tag{1}
> $$
> 且对于任意的正整数 $k < n$：
> $$
> \sum_{i=1}^{k} s_i > \frac{1}{2} k (k-1) \tag{2}
> $$
>

**证明：** 类似非强连通图的证明。不等式 (1) 显然成立。前 $k$ 个节点形成子竞赛图，而因为强连通性，所以必存在其指向后 $n-k$ 个节点的边，故有不等式 (2) 成立。


### 定理 10

> 若竞赛图 $\mathcal{T}$ 的得分序列为 $s_1\le s_2\le \cdots \le s_n$，那么对于任意的正整数 $k\le n$，有 $\frac{k-1}{2} \le s_k \le \frac{n+k-2}{2}$

**证明：** 由得分序列的性质(2)可知第一个不等号成立。因为竞赛图的反图仍是竞赛图，所以第二个不等号成立。


接下来的定理给出了竞赛图中节点的得分与其所在的强连通分量的关系。


### 定理 11

> 令 $v_i$ 与 $v_j$ 表示竞赛图 $\mathcal{T}$ 中不同强连通分量中的两节点，$\mathcal{T}$ 中存在边 $(v_i,v_j)$ 当且仅当 $s_i > s_j$

**证明：** 
节点 $v_i$ 指向 $v_j$ 说明缩点后 $v_i$ 所在强连通分量将指向 $v_j$ 所在的强连通分量。因为缩点后的竞赛图满足传递性，所以 $v_i$ 将指向所有 $v_j$ 指向的点。又因为 $v_i$ 指向 $v_j$，所以有 $s_i > s_j$。

若 $s_i > s_j$，假设 $v_j$ 指向 $v_i$，那么可知 $s_j > s_i$，矛盾。因此，必有 $v_i$ 指向 $v_j$


以上定理说明了，竞赛图中节点的得分与其所在连通分量的位置是对应的。同时，可以得到以下推论：


### 推论 11a

> 竞赛图中得分相同的点在同一强连通分量中。


而对于得分不同的点，下面的定理给出了其在同一强连通分量中的充分条件：


### 定理 12

> 竞赛图 $\mathcal{T}$ 的得分序列为 $s_1\le s_2\le \cdots \le s_n$ 。若 $0 \le s_p - s_q <\frac{p-q+1}{2}$，那么 $v_p$ 与 $v_q$ 在同一强连通分量内。

**证明：** 记 $v_p$ 指向的点中不与 $v_p$ 在同一强连通分量内的标号最大的点为 $v_j$ 。由定理 10可知，在 $v_p$ 所在的连通分量中， $v_p$ 的得分不低于 $\frac{p-j-1}{2}$ 。又由定理 11可知， $v_p$ 指向所有得分不超过 $s_j$ 的点。所以， $s_p \ge \frac{p-j-1}{2} + j = \frac{p+j-1}{2}$ 。

若 $v_q$ 不在 $v_p$ 的强连通分量内，则 $v_q$ 必属于集合 $\{v_1,v_2,...,v_j\}$，由定理 10， $s_q \le \frac{j+q-1}{2}$ 。综合上述不等式，有 
$$
\frac{p-q+1}{2} > s_p - s_q \ge  \frac{p+j-1}{2} - \frac{j+q-1}{2} = \frac{p-q+1}{2}
$$

矛盾。因此 $v_p$ 与 $v_q$ 属于同一强连通分量。


由定理 12易得下面两个判断竞赛图强连通性的充分条件：

### 推论 12a

> 若竞赛图 $\mathcal{T}$ 中任意两点之间的的分差均小于 $\frac{1}{2} n$，则 $\mathcal{T}$ 是强连通的。

### 推论 12b

> 若竞赛图 $\mathcal{T}$ 中所有节点的入度与出度均不低于 $\frac{p-1}{4}$，则 $\mathcal{T}$ 是强连通的。

------

## 图的计数

最后，我们给出节点数为 $n$ 的竞赛图与强连通图的计数公式。在此之前，我们先给出一个重要的推论：

### 推论 5b

> 强连通竞赛图对强连通分量缩点后得到的图对应一个全序关系。

这个推论是显然的，它将在之后的推导中起到重要的作用。

令 $T_n$ 表示 $n$ 个点的竞赛图数量，其生成函数为 
$$
T(x) = \sum_{n=1}{\infty} T_n x^n
$$

因为竞赛图的数量对应于定向 $\frac{n(n-1)}{2} $ 条边的方案数，是比较容易求得的。借助推论 5b，我们可建立强连通竞赛图数量的生成函数 $S(x)$ 与 $T(x)$ 的关系。

首先，将 $T(x)$ 写作 $T(x) = \sum_{n=1}{\infty} T_n(x)$，其中 $T_n(x)$ 表示强连通分量数目为 $n$ 的竞赛图个数。显然，$T_n(x) = [S(x)]^n$ 。因此，可得到

$$
S(x) = \frac{T(x)}{1+T(x)}
$$

------



## 参考资料
> - Bondy, John Adrian, and Uppaluri Siva Ramachandra Murty. *Graph theory with applications*. Vol. 290. London: Macmillan, 1976.
> - Harary, Frank , and L. Moser . "The Theory of Round Robin Tournaments." *American Mathematical Monthly*73.3(1966):231-246.
