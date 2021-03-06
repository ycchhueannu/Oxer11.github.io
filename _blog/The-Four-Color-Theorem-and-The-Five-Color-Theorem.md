---
title: The Four-Color Theorem and The Five-Color Theorem
toc: true
date: 2018-12-29 14:40:47
tags: [Graph Theory]
categories: 
- Graph Theory
- Chapter 11  The Four-Color Problem
mathjax: true
---

在1852年Hamilton写给De Morgan的一封信中，首次提到了由他的学生Francis Guthrie提出的四色问题。在经历了一个世纪的不断探索后，终于，四色定理在1977年被Appel和Haken证明。本篇主要讨论四色定理和它的几个等价命题，并给出五色定理的证明。

------

#### 猜想 11.1/定理 11.2   四色定理（面）

> 没有割边的平面图是4-面可着色的。  
>

------

四色定理作为一个经典的难题，证明比较复杂，此处省略。但对于四色定理的研究，却引出了许多看似不相关但却与四色定理等价的命题。

------

#### 猜想 11.3  四色定理（点） 

> 无自环的平面图是4-点可着色的。

**证明：** 平面图中的点可对应其对偶图中的面。若四色定理对对偶图成立，则猜想11.3对原图成立。

------

#### 猜想 11.5  四色定理（边）   

> 3-连通的三次平面图是3-边可着色的。
> 其中，三次图指度数为3的正则图。

------

边着色与面着色看似关联不大，但是Tait在1880年发现了二者之间不可思议的关联。上述猜想的证明，可以直接由以下定理推出。

------

#### 定理 11.4  Talt 定理   

> 3-连通的三次平面图是4-面可着色的，当且仅当它是3-边可着色的。

**证明：** 记图 $G$ 为任意3-连通的三次平面图。

若图 $G$ 是4-面可着色的，记四种颜色为 $\alpha_0=(0,0),\alpha_1=(1,0),\alpha_2=(0,1),\alpha_3=(1,1)$。

三次图中所有节点的度数均为3，故至多与三个面相邻，记它们的颜色分别为 $\alpha_i,\alpha_j,\alpha_k$。

![Figure11.2](\images\Figure11.2.png)

如上图进行边着色，每条边恰好分隔两个面，规定边的颜色为其分隔的两个面的颜色之和。其中，$\alpha_i + \alpha_j$ 是定义在模2意义下的向量加法。

因为相邻两个面的颜色不同，所以二者相加不可能得到颜色 $\alpha_0$。可以验证，三种不同的面颜色得到的边着色恰好是 $\alpha_1,\alpha_2,\alpha_3$ 三种颜色，故得到一种合法的边着色方案。



若图 $G$ 是3-边可着色的，记三种颜色分别为 $1,2,3$。

![Figure11.3](\images\Figure11.3.png)

考虑由颜色为 $1$ 和 $2$ 的边导出的子图 $G_{12}$，因为每个顶点相邻的边颜色不同，所以在导出子图 $G_{12}$ 中每个点度数为2，说明 $G_{12}$ 是由若干个环构成的。此时，图中必然存在一种2-面着色方案，如图11.3(b)所示。

再考虑由颜色为 $1$ 和 $3$ 的边导出的子图 $G_{13}$，同理，也存在一种2-面着色方案。图 $G$ 中的每个面都由颜色为 $1,2,3$ 的边围成，每个图 $G$ 中的面都可看作是子图 $G_{12}$ 和 $G_{13}$ 的交。组合两个子图中的两种颜色，即可得到图 $G$ 中的4-面着色方案，如图11.3(c)。

------

如果一个三次图是哈密顿图，那么可将哈密顿回路上的边依次染成两种不同的颜色。因为图中每个点的度数为3，所以剩下的边必然是不相邻的，可以用第3种颜色染色。因此，三次的哈密顿图是3-边可着色的。若能证明所有的3-连通三次平面图都是哈密顿图，那么就便证明四色定理。

借助以上结论，Tait在1880年时，认为自己已经证出了四色定理。然而，直到半个世纪之后，Tutte(1946)构造了一个非哈密顿图的3-连通三次平面图，驳倒了Tait的证明。

Kempe在1879年也声称自己完成了四色定理的证明，可是在11年后Heawood发现了证明中的漏洞。尽管如此，Kempe的方法仍可以被用来证明五色定理。

------


#### 定理 11.6  五色定理   

> 任意无自环的平面图是5-点可着色的。

**证明：** 记平面图为图 $G$，对图中节点数进行归纳。由推论10.22可知，图 $G$ 存在度数不超过5的节点，记作点 $v$。

由归纳假设，图 $H = G -v$ 是5-点可着色的。

若与节点 $v$ 相邻的节点中，有不超过4种不同的颜色，则将点 $v$ 染成第5种颜色，即得到一种5-点着色方案。

若与节点 $v$ 相邻的节点恰好有5种不同的颜色，按在平面上与 $v$ 连边的顺序，将这五个点依次记为 $v_1,v_2,v_3,v_4,v_5$，点 $v_i$ 的颜色记为 $i$ 。

考虑由颜色为 $1$ 和 $3$ 的点导出的子图 $G_{13}$，图 $G_{13}$ 中每个节点的度数不超过2，所以每个连通分支只可能是环或链。若点 $v_1$ 与 点 $v_3$ 属于不同连通分支，则将点 $v_1$ 所在连通分支中所有节点的颜色互换，可得到一种新的染色方案，使得点 $v_1$ 颜色是 $3$ 。此时，只需将点 $v$ 染成颜色 $1$ 即可。

若点 $v_1$ 与点 $v_3$ 属于相同连通分支，则图 $G$ 中存在一条点 $v_1$ 到点 $v_3$ 的路径 $P_{13}$。此时，对由颜色为 $2$ 和 $4$ 的点导出的子图 $G_{24}$ 。若点 $v_2$ 与 $v_4$ 属于不同连通分支，则将点 $v_2$ 所在连通分支中所有节点颜色互换，并将点 $v$ 染成 颜色 $2$。

若点 $v_2$ 与 $v_4$ 也属于相同连通分支，则图 $G$ 中存在一条 $v_2$ 到 $v_4$ 的路径 $P_{24}$ 。如下图所示，路径 $P_{13}$ 与路径 $P_{24}$ 相交，与图 $G$ 是平面图矛盾。

![Theorem11.6](\images\Theorem11.6.png)

因此，平面图 $G$ 是5-点可着色的。

------



## 参考资料

> - Bondy, John Adrian, and Uppaluri Siva Ramachandra Murty. *Graph theory with applications*. Vol. 290. London: Macmillan, 1976.
> - Appel, Kenneth, and Wolfgang Haken. "The solution of the four-color-map problem." *Scientific American* 237.4 (1977): 108-121.
> - Tutte, William Thomas. "On hamiltonian circuits." *Journal of the London Mathematical Society* 1.2 (1946): 98-101.
> - Tait, Peter Guthrie. "Remarks on the colouring of maps." *Proc. Roy. Soc. Edinburgh*. Vol. 10. No. 729. 1880.
> - Kempe, Alfred B. "On the geographical problem of the four colours." *American journal of mathematics* 2.3 (1879): 193-200.
> - Heawood, Percy John. "Map color theorems." *Quant. J. Math.*24 (1890): 332-338.
