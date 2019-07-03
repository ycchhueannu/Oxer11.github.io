---
title: Graphic Sequence
toc: true
date: 2018-12-30 14:44:50
tags: [Graph Theory]
categories: 
- Graph Theory
- Chapter 01  Graphs
mathjax: true
---

若图 $G$ 中节点 $v_1,v_2,...,v_n$ 的度数为 $d(v_1),d(v_2),...,d(v_n)$，则序列 $(d(v_1),d(v_2),...,d(v_n))$ 称作图 $G$ 的度数序列。给定一个序列，若存在图 $G$ 的度数序列与给定序列相同，则称该序列是可图化的。判断序列的可图化是图论中的基本问题，下面的定理给出了解答。

------

#### 练习 1.1.16   Degree Sequence

> 序列 ${\bf d}=(d_1,d_2,...,d_n)$ 是非增的非负整数序列，即 $d_1 \ge d_2 \ge ... \ge d_n \ge 0$ ，那么：
>
> a) 序列 ${\bf d}$ 是可图化的，当且仅当 $\sum_{i=1}^{n} d_i$ 是偶数。
>
> b) 序列 ${\bf d}$ 是无自环的图的度数序列，当且仅当 $\sum_{i=1}^{n} d_i$ 是偶数且 $d_1 \le \sum_{i=2}^{n} d_i$ 。

**证明：** 

a) 对 $\sum_{i=1}^n d_i$ 归纳。当 $\sum_{i=1}^n d_i = 0$ 时，构造 $n$ 个节点的零图即可。

若存在节点 $i$ 的度数 $d_i$ 为奇数，因为 $\sum_{i=1}^n d_i$ 是偶数，所以必存在节点 $j(j \neq i)$ 的度数 $d_j$ 也为奇数。由归纳假设，序列 ${\bf d'}=(...,d_i-1,...,d_j-1,...)$ 是可图化的，在该图中加入边 $ij$ 后得到的图即为所求。 

若所有节点的度数均为偶数，则在节点 $i$ 处加入 $d_i/2$ 个自环得到的图即为所求。

b) 对 $\sum_{i=1}^n d_i$ 归纳。当 $\sum_{i=1}^n d_i = 0$ 时，构造 $n$ 个节点的零图即可。

先去掉末尾结尾度数为0的节点，它们在图中是孤立点，对边的构造无影响。仍记剩下的节点数为 $n$。

当 $n=2$ 时，必有 $d_1 = d_2$，故在节点 $1$ 和节点 $2$ 之间连 $d_1/2$ 条边得到的图即为所求。

当 $n \ge 3$ 时，考虑序列 ${\bf d'}$ 为序列 $(d_1 -1, d_2, d_3-1, ..., d_n)$ 降序排序后得到的序列。

若 $d_1 > d_2$，则 ${\bf d'}=(d_1 -1, d_2, d_3-1, ..., d_n)$，且成立

$$
\sum_{i=1}^n d'_i = \sum_{i=1}^n d_i -2
$$
和 
$$
d'_1 = d_1 -1 \le \sum_{i=2}^n d_i -1 = \sum_{i=2}^n d'_i
$$

 由归纳假设，序列 ${\bf d'}$ 是可图化的，在相应图上加入边 $13$ 即可。

若 $d_1 = d_2$，则有 

$$
d'_1 = d_2 = d_1 \le \sum_{i=2}^{n} d_i -2 =  \sum_{i=2}^{n} d'_i 
$$

因为，$n\ge 3$ 且 $\sum_{i=1}^n d_i$ 是偶数，所以有中间的不等号成立。 由归纳假设，序列 ${\bf d'}$ 是可图化的，在相应图上加入边 $13$ 即可。

------

若简单图 $G$ 的度数序列为 ${\bf d}$，则称序列 ${\bf d}$ 是可简单图化的(graphic)。以下两个定理给出了判断序列是否可简单图化的充要条件。

------

#### 练习 1.1.19 Graphic Sequence   

> 序列 ${\bf d}=(d_1,d_2,...,d_n)$ 是非增的非负整数序列，令 
>
>$$
> {\bf d'} = (d_2 -1, d_3-1,...,d_{d_1+1}-1,d_{d_1+2},...,d_n)
>$$
>
> 则序列 ${\bf d}$ 是可简单图化的，当且仅当序列 ${\bf d'}$ 是可简单图化的。

**证明：** 若序列 ${\bf d'}$ 是可简单图化的，令图 $G$ 的度数序列为 ${\bf d'}$，记序列 ${\bf d'}$ 对应的节点分别为 $v_2,v_3,...,v_n$。在图 $G$ 中加入节点 $v_1$，同时加入边 $v_1v_2,v_1v_3,...,v_1v_{d_1+1}$，得到的图即为所求。

若序列 ${\bf d}$ 是可简单图化的，令图 $G$ 的度数序列为 ${\bf d}$，记序列 ${\bf d'}$ 对应的节点为 $v_1,v_2,...,v_n$。

若点 $v_1$ 恰与点 $v_2,v_3...,v_{d_1+1}$ 相邻，则图 $G-{v_1}$ 即为所求。

若不然，在不改变节点度数的前提下，对图 $G$ 的边进行调整，使点 $v_1$ 与点 $v_2,v_3,...,v_{d_1+1}$ 相邻。

记第一个不与 $v_1$相邻的节点为 $v_i$ ，最后一个与 $v_1$ 相邻的节点为 $v_j$。

若 $i>d_1+1$，则当前的图已符合要求。

若 $i \le d_1+1$，因为 $d_i \ge d_j$，而 $v_j$ 与 $v_1$ 相邻， $v_i$ 不与 $v_1$ 相邻，所以存在节点 $v_k$ 与 $v_i$ 相邻，但不与 $v_j$ 相邻。在图 $G$ 中删去边 $v_1 v_j$ 和 $v_iv_k$，加入边 $v_1v_i$ 和 $v_jv_k$ ，可保持图中节点度数不变，且使 $v_1$ 与 $v_i$ 相邻。重复该调整过程，直到 $i>d_1+1$，此时的图已符合要求。

------

#### 练习 1.1.18 Erdős and Gallai's Theorem   

> 序列 ${\bf d}=(d_1,d_2,...,d_n)$ 是非增的非负整数序列，则序列 ${\bf d}$ 是可简单图化的当且仅当 $\sum_{i=1}^n d_i$ 是偶数且满足
> $$
> \sum_{i=1}^k d_i \le k(k-1) + \sum_{i=k+1}^n min\{k,d_i\}, \quad 1\le k\le n 
> $$
>

**证明：**

必要性。 若存在简单图的度数序列为 ${\bf d}$，对于 $1\le k\le n$，不等式左侧为前 $k$ 个节点的度数之和。

考虑不等式右侧的两项。前 $k$ 个节点之间的边对度数的贡献为 $k(k-1)$，前 $k$ 个节点与后 $n-k$ 个节点之间的边对度数的贡献不会超过 $\sum_{i=k+1}^n min\{k,d_i\}$，只需考虑后 $n-k$ 个节点每个节点的度数即得。故不等式成立。

充分性。通过不断加边调整得到答案。记调整过程中度数序列为 $(d(v_1),d(v_2),...,d(v_n))$，其中 $d(v_i)\le d_i$，$n$ 个不等式等号均成立时的图即为所求。记第一个不满足 $d(v_i)\neq d_i$的节点编号为 $r$。初始时，$d(v_i)=0$。

加边过程保证度数序列的字典序增加，即不改变 $d(v_i)(1\le i<r)$ 的值，同时使 $d(v_r)$ 增大。

加边过程保证 $\{v_{r+1},...,v_n\}$ 之间不存在边，所有的边都与前 $r$ 个节点相关。

加边过程分为以下四种情况：

Case 0：存在与 $v_r$ 不相邻的节点 $v_i$，满足  $d(v_i)<d_i$，加入边 $v_r v_i$

Case 1：存在与 $v_r$ 不相邻的节点 $v_i$，但 $i<r$，此时， $d(v_i)=d_i$，需要先对点 $v_i$ 进行调整。因为 $d(v_i) = d_i\ge d_r >d(v_r)$，所以存在节点 $u$ 与 $v_i$ 相邻，但不与 $v_r$ 相邻。

​	若 $d_r - d(v_r) \ge 2$，则删去边 $uv_i$，并加入边 $uv_r$ 和 $uv_i$

​	若 $d_r - d(v_r)=1$，因为 $\sum_{i=1}^n d_i$ 和 $\sum_{i=1}^n d(v_i)$ 都是偶数，所以必存在不同于 $u$ 的一点 $v_k$，满				 足 $d(v_k)<d_k$。若 $v_k$ 与 $v_r$ 不相邻，则适用于 Case 0 条件。若 $v_k$ 与 $v_r$ 相邻，则删去边 $uv_i$ 和 $v_rv_k$，并加入边 $v_iv_r$ 和 $uv_r$ 。因为 $d(v_k)<d_k$，所以点 $v_k$ 不是前 $r-1$ 个节点，调整操作不改变前 $r-1$ 个节点的度数。

Case 2：若前 $r-1$ 个节点均与节点 $v_r$ 相邻，但存在节点 $v_k$，$d(v_k) < min\{r,d_k\}$。说明节点 $v_k$ 在 $v_r$ 之后，且前 $r$ 个节点中有与 $v_k$ 不相邻的节点，记该节点为 $v_i$。 因为 $d(v_i)>d(v_r)$，所以存在节点 $u$ 与 $v_i$ 相邻，但不与 $v_r$ 相邻。删去边 $uv_i$，并加入边 $v_iv_k$ 和 $uv_r$

Case 3：若前 $r-1$ 个节点均与节点 $v_r$ 相邻，但其中某两个节点 $v_i$ 与 $v_j$ 不相邻。因为 $d(v_i)>d(v_r)$ 且 $d(v_j)>d(v_r)$，所以存在节点 $u$ 与 $v_i$ 相邻，但不与 $v_r$ 相邻，存在节点 $w$ 与 $v_j$ 相邻，但不与 $v_r$ 相邻。若 $u$ 或 $v$ 是前 $r-1$ 个节点之一，则适用于 Case 1 条件。若不然，则删去边 $uv_i$ 和 $wv_j$，并加入边 $v_iv_j$ 和 $uv_r$

 若以上四种情况均不满足，则说明前 $r$ 个节点两两相邻，且与后 $n-r$ 个节点已连接尽可能多的连边，故 $\sum_{i=1}^r d(v_i) = r(r-1) + \sum_{i=r+1}^{n} d_i \ge \sum_{i=1}^r d_i$，前 $r$ 个节点均已满足要求。令 $r++$，继续该过程。因为每次调整序列字典序都会增加，而字典序上界即为 ${\bf d}$，所以不断重复上述过程后，必能得到度数序列 ${\bf d}$。

**总结**：证明的核心是四种加边调整的方式。通过必要性的证明，容易发现，等号成立时，前 $r$ 个节点构成完全图，且与后 $n-r$ 个节点尽可能多的相连。Case 0 和 Case 2 对应使 $v_r$ 尽可能与后面的节点相连，Case 1 和 Case 3 则对应使前 $r$ 个节点之间尽可能多的连边。

------

以上定理的证明过程同时给出了构造简单图的方法。除此之外，Sierksma等人与1991年总结了七个可简单图化的充要条件，而Iványi，Antal和Loránd Lucz三人与2011年提出了判断序列是否可简单图化的线性算法。至此，可简单图化的问题已基本解决。

## 参考资料

> - Bondy, John Adrian, and Uppaluri Siva Ramachandra Murty. *Graph theory with applications*. Vol. 290. London: Macmillan, 1976.
> - Iványi, Antal, and Loránd Lucz. "Erdos-Gallai test in linear time." *Combinatorica* (2011): 4.
> - Sierksma, Gerard, and Han Hoogeveen. "Seven criteria for integer sequences being graphic." *Journal of Graph theory*15.2 (1991): 223-231.
> - Tripathi, Amitabha, Sushmita Venugopalan, and Douglas B. West. "A short constructive proof of the Erdős–Gallai characterization of graphic lists." *Discrete Mathematics* 310.4 (2010): 843-844.