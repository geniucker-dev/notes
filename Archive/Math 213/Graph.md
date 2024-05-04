# 涩**图**

- A graph consists of a set of vertices $V$, $\left\vert V \right\vert = n$  
- and a set of edges $E$, $\left\vert E \right\vert = m$  
- Each edge has two **endpoints**  
- An edge **joins** its endpoints, two vertices are **adjacent** if they are joined by an edge  
- When a vertex is an endpoint of an edge, we say that the edge and the vertex are **incident** to each other.  

## Simple Graph, Multigraph, Pseudograph
### simple graph (简单图)
A graph in which each edge connects two **different** vertices and where **no** two edges connect the same pair of vertices.  
意思是说，简单图中没有重复的边，也没有自环。  
![[assets/Graph_1.png]]

### multigraph (多重图)
Graphs that may have **multiple edges** connecting the same vertices.  
可能存在多条边连接相同顶点的图。  
![[assets/Graph_2.png]]

### pseudograph (伪图)
Graphs that may include **loops**, and possibly multiple edges connecting the same pair of vertices or a vertex to itself.
可能存在自环，也可能存在多条边连接相同顶点的图。
![[assets/Graph_3.png]]

## Undirected Graph
### 一些定义和记号
- 如果两个顶点之间存在边，那么这两个顶点是**adjacent**的或者说是**neighbors**  
- $N(v)$: 如果$v$是$G=(V, E)$中的一个顶点，那么$N(v)$是与$v$相邻的顶点的集合。  
- $N(A)$: 如果$A$是$G=(V, E)$的一个子集，那么$N(A)$是与$A$中的顶点相邻的顶点的集合。  
- $deg(v)$: 无向图的**degree**是指与$v$相邻的顶点的个数，但是一个环对degree的贡献是2。    

### Theorem (Handshaking Theorem)
If $G = (V, E)$ is an **undirected** graph with $m$ edges, then
$$2m=\sum_{v\in V}deg(v)$$
如果一个无向图有$m$条边，那么这个图中所有顶点的度数之和为$2m$（即使是有多重边或自环的图）。

### Theorem
An undirected graph has an **even** number of vertices of **odd** degree.  
一个无向图中，度数为奇数的顶点的个数为偶数。  
证明：
假设$V_{odd}$是所有度数为奇数的顶点的集合，$V_{even}$是所有度数为偶数的顶点的集合，那么
$$2m=\sum_{v\in V}deg(v)=\sum_{v\in V_{odd}}deg(v)+\sum_{v\in V_{even}}deg(v)$$
由于$2m$是偶数，$\sum_{v\in V_{even}}deg(v)$也是偶数，所以$\sum_{v\in V_{odd}}deg(v)$必须也是偶数，而$\sum_{v\in V_{odd}}deg(v)$是所有度数为奇数的顶点的度数之和，所以度数为奇数的顶点的个数为偶数。  

## Directed Graph
### 一些定义和记号
- 每一条边都是一个有序对$(u, v)$，这条边的方向是从$u$指向$v$  
- 假设$(u, v)$是$G=(V, E)$中的一条边，那么$u$是**initial vertex**并且**adjacent to $v$**，$v$是**terminal vertex**并且**adjacent from $u$**  
- $deg^-(v)$: **in-degree** of $v$，指向$v$的边的条数  
- $deg^+(v)$: **out-degree** of $v$，从$v$出发的边的条数
- 环对in-degree和out-degree的贡献都是1  

### Theorem
Let $G = (V, E)$ be a graph with directed edges. Then,  
$$\left\vert E \right\vert = \sum_{v\in V}deg^-(v)=\sum_{v\in V}deg^+(v)$$
有向图的边的条数等于所有顶点的in-degree之和，也等于所有顶点的out-degree之和。  

## Complete Graphs (完全图)
A **complete graph** on n vertices, denoted by $K_N$, is the simple graph that contains exactly one edge between each pair of distinct vertices.  
**complete graph**是一个简单图，它的任意两个顶点之间都有一条边。  
![[assets/Graph_4.png]]  

## Cycles
A **cycle** $C_n$ for $n\geq 3$ consists of $n$ vertices $v_1, v_2, \cdots, v_n$, and edges $\{v_1, v_2\}, \{v_2, v_3\}, \cdots, \{v_{n-1}, v_n\}, \{v_n, v_1\}$.  
**cycle**包含$n$个顶点$v_1, v_2, \cdots, v_n$，以及$n$条边$\{v_1, v_2\}, \{v_2, v_3\}, \cdots, \{v_{n-1}, v_n\}, \{v_n, v_1\}$。  
![[assets/Graph_5.png]]  

## Wheels
A **wheel** $W_n$ is obtained by adding an additional vertex to a cycle $C_n$.  
**wheel**是在一个cycle $C_n$上再加一个顶点。  
![[assets/Graph_6.png]]

## N-dimensional Hypercube
<!-- An n-dimensional hypercube, or n-cube, Qn is a graph with 2n
-->
An **n-dimensional hypercube**, or **n-cube**, $Q_n$ is a graph with $2^n$ vertices representing all bit strings of length $n$, where there is an edge between two vertices that **differ in exactly one bit position**.  
**n-dimensional hypercube**或者**n-cube**是一个图，它有$2^n$个顶点，每个顶点代表一个长度为$n$的bit string，如果两个顶点的bit string**只有一个**bit不同，那么这两个顶点之间有一条边。  
![[assets/Graph_7.png]]  
有多少条边：  
为了从$n$-cube $Q_n$构造$(n+1)$-cube $Q_{n+1}$，我们需要两个$Q_n$，一个$Q_n$的顶点的标签前面加一个0，另一个$Q_n$的顶点的标签前面加一个1，然后把两个$Q_n$中标签只有第一位不同的顶点之间加一条边。  

## Bipartite Graphs (二分图)
Definition: A simple graph $G$ is **bipartite** if $V$ can be partitioned into two disjoint subsets $V_1$ and $V_2$ such that **every edge** connects a vertex in $V_1$ and a vertex in $V_2$.  
An equivalent definition of a bipartite graph is a graph where it is possible to color the vertices red or blue so that **no two adjacent vertices** are of the same color.  
定义：一个简单图$G$是**二分图**，如果$V$可以被划分为两个不相交的子集$V_1$和$V_2$，并且**每条边**都连接一个$V_1$中的顶点和一个$V_2$中的顶点。  
一个等价的定义是，如果可以把图中的顶点染成红色和蓝色，使得**任意两个相邻的顶点**颜色不同，那么这个图是二分图。  
![[assets/Graph_8.png]]

### Bipartite and not bipartite
- **Bipartite**: Its vertex set is the union of two disjoint sets, **$\{a, b, d\}$ and $\{c, e, f , g\}$**, and each edge connects a vertex in one of these subsets to a vertex in the other subset.  
- **Not bipartite**: Its vertex set cannot be partitioned into two subsets so that edges do not connect two vertices from the same subset.

### Complete Bipartite Graphs (完全二分图)
Definition: A **complete bipartite graph** $K_{m,n}$ is a graph that has its vertex set partitioned into two subsets $V_1$ of size $m$ and $V_2$ of size $n$ such that there is an edge from **every** vertex in $V_1$ to **every** vertex in $V_2$.  
定义：一个**完全二分图**$K_{m,n}$是一个图，它的顶点集被划分为两个子集$V_1$和$V_2$，$V_1$的大小为$m$，$V_2$的大小为$n$，并且$V_1$中的每个顶点都与$V_2$中的每个顶点都有一条边。  
![[assets/Graph_9.png]]  

### Bipartite Graphs and Matchings
**Matching**是指把一个集合中的元素和另一个集合中的元素匹配起来。一个matching是边集的一个子集，使得任意两条边都不与同一个顶点关联。换句话说，一个matching是边集的一个子集，使得如果$\{s,t\}$和$\{u,v\}$是matching的两条边，那么$s, t, u, v$都是不同的。  

**Job assignments**：顶点代表工作和员工，边连接员工和他们被训练过的工作。一个常见的目标是把工作分配给员工，使得完成的工作最多。  

A **maximum matching** is a matching with the **largest number of edges**.  
一个**maximum matching**是一个matching，它的边数最多。  

A matching $M$ in a bipartite graph $G = (V, E)$ with bipartition $(V_1, V_2)$ is a **complete matching** from $V_1$ to $V_2$ if every vertex in $V_1$ is the endpoint of an edge in the matching, or equivalently, if $\left\vert M \right\vert = \left\vert V_1 \right\vert$.  
一个matching $M$是一个**complete matching**，如果$M$是从$V_1$到$V_2$的matching，并且$V_1$中的每个顶点都是$M$中一条边的端点，或者等价地，如果$\left\vert M \right\vert = \left\vert V_1 \right\vert$。  

**Theorem (Hall’s Marriage Theorem)**: The bipartite graph $G = (V, E)$ with bipartition $(V_1, V_2)$ has a complete matching from $V_1$ to $V_2$ if and only if $\left\vert N(A) \right\vert \geq \left\vert A \right\vert$ for all subsets $A$ of $V_1$.  
**Hall’s Marriage Theorem**：如果一个二分图$G = (V, E)$，它的顶点集被划分为两个子集$V_1$和$V_2$，那么$G$有一个从$V_1$到$V_2$的complete matching，当且仅当对于$V_1$的任意子集$A$，$\left\vert N(A) \right\vert \geq \left\vert A \right\vert$。  

## Subgraphs
Definition: A **subgraph** of a graph $G = (V, E)$ is a graph $(W , F)$, where $W \subseteq V$ and $F \subseteq E$.  
定义：图$G = (V, E)$的一个**subgraph**是一个图$(W , F)$，其中$W \subseteq V$并且$F \subseteq E$。  
![[assets/Graph_10.png]]  

## Union of Graphs
Definition: The **union** of two simple graphs $G_1 = (V_1, E_1)$ and $G_2 = (V_2, E_2)$ is the simple graph with vertex set $V_1 \cup V_2$ and edge set $E_1 \cup E_2$, denoted by $G_1 \cup G_2$.  
定义：两个简单图$G_1 = (V_1, E_1)$和$G_2 = (V_2, E_2)$的**union**是一个简单图，它的顶点集是$V_1 \cup V_2$，边集是$E_1 \cup E_2$，记作$G_1 \cup G_2$。  
![[assets/Graph_11.png]]  

## 图的表示
- adjacency list (邻接表)  
- adjacency matrix (邻接矩阵)
- incidence matrix (关联矩阵)

### Adjacency List (邻接表)
定义：adjacency list (邻接表)可以用来表示一个**没有重复边**的图，它指定了每个顶点的邻接顶点。  

### Adjacency Matrix (邻接矩阵)
### 简单图的邻接矩阵
定义：假设$G = (V, E)$是一个**简单图**，$\left\vert V \right\vert = n$。任意地把$G$的顶点列出来，$v_1, v_2, \cdots, v_n$。$G$的**adjacency matrix** $A_G$是一个$n\times n$的0-1矩阵，当$v_i$和$v_j$是adjacent的时候，$A_G$的$(i, j)$位置是1，当$v_i$和$v_j$不是adjacent的时候，$A_G$的$(i, j)$位置是0。  
$$A_G=\left[a_{ij}\right]\text{,where}$$
$$
a_{ij}=\begin{cases}
1 & \text{if }v_i\text{ and }v_j\text{ are adjacent}\\
0 & \text{if }v_i\text{ and }v_j\text{ are not adjacent}
\end{cases}
$$
![[assets/Graph_12.png]]  
### 有环或多重边的图的邻接矩阵
邻接矩阵也可以用来表示**有环或多重边的图**。邻接矩阵不再是0-1矩阵。$a_{ij}$的值是$v_i$和$v_j$之间的边的条数。  
![[assets/Graph_13.png]]  

### Incidence Matrix (关联矩阵)
定义：假设$G = (V, E)$是一个**无向图**，顶点$v_1, v_2, \cdots, v_n$，边$e_1, e_2, \cdots, e_m$。$G$的**incidence matrix** $M_G$是一个$n\times m$的0-1矩阵$M=\left[m_{ij}\right]$，
$$
m_{ij}=\begin{cases}
1 & \text{if }e_j\text{ is incident with }v_i\\
0 & \text{otherwise}
\end{cases}
$$
![[assets/Graph_14.png]]  
![[assets/Graph_15.png]]  

## Isomorphism of Graphs (同构)
定义：简单图$G_1 = (V_1, E_1)$和$G_2 = (V_2, E_2)$是**isomorphic**的，如果存在一个从$V_1$到$V_2$的**双射**，并且满足对于$V_1$中的任意两个顶点$a$和$b$，$a$和$b$是adjacent的当且仅当$f(a)$和$f(b)$是adjacent的。这样的函数$f$被称为**isomorphism**。  
举个例子，下面的两个图是isomorphic的  
![[assets/Graph_16.png]]
双射函数可以是$f(u_1)=v_1, f(u_2)=v_4, f(u_3)=v_3, f(u_4)=v_2$。  

验证两个图是isomorphic是较为困难的  
但是，如果两个图不是isomorphic的，那么可以通过检查两个图的一些**invariants**来证明  
常见的invariants有：  
- number of vertices (顶点的个数)  
- number of edges (边的条数)  
- degree sequence (度数序列)  
- etc.  

### 例1
下面两个是不是isomorphic的？  
![[assets/Graph_17.png]]  
H有度数为1的顶点(e)，而G没有，所以不是isomorphic的。  

### 例2
下面两个是不是isomorphic的？  
![[assets/Graph_18.png]]  
G和H不是isomorphic的。因为G中的顶点a的度数是2，而a必须对应于H中的t, u, x, 或y。然而，H中的这四个顶点中的每一个都与H中的另一个度数为2的顶点相邻，而这对于G中的a来说是不正确的。  

### 例3
下面两个是不是isomorphic的？  
![[assets/Graph_19.png]]  
$f(u_1)=v_6, f(u_2)=v_3, f(u_3)=v_4, f(u_4)=v_5, f(u_5)=v_1, f(u_6)=v_2$  
我们也看看邻接矩阵：  
![[assets/Graph_20.png]]  
所以是一个isomorphism。

## Path: Undirected Graph
<!-- Definition: Let n be a nonnegative integer and G an undirected graph. A
path of length n from u to v in G is a sequence of n edges e1, e2, . . . ,
en of G for which there exists a sequence x0 = u, x1, . . . , xn−1, xn = v
of vertices such that ei has the endpoints xi−1 and xi
for i = 1, ..., n. -->
Definition: Let $n$ be a nonnegative integer and $G$ an **undirected** graph. **A path of length $n$ from $u$ to $v$** in $G$ is a sequence of $n$ edges $e_1, e_2, \cdots, e_n$ of $G$ for which there exists a sequence $x_0 = u, x_1, \cdots, x_{n-1}, x_n = v$ of vertices such that $e_i$ has the endpoints $x_{i-1}$ and $x_i$ for $i = 1, \cdots, n$.  
定义：$n$是一个非负整数，$G$是一个**无向图**。$G$中从$u$到$v$的**长度为$n$的path**是一个边的序列$e_1, e_2, \cdots, e_n$，满足存在一个顶点的序列$x_0 = u, x_1, \cdots, x_{n-1}, x_n = v$，使得$e_i$的端点是$x_{i-1}$和$x_i$，$i = 1, \cdots, n$。  

一个path被称作**circuit**或cycle，如果它的起点和终点是同一个顶点，但长度大于0。  

一个path或者circuit是**simple**的，如果它不包含重复的edge。  

path的长度=path里面的边的条数  

## Path: Directed Graph
Definition: Let $n$ be a nonnegative integer and $G$ an **directed** graph. **A path of length $n$ from $u$ to $v$** in $G$ is a sequence of $n$ edges $e_1, e_2, \cdots, e_n$ of $G$ for which there exists a sequence $x_0 = u, x_1, \cdots, x_{n-1}, x_n = v$ of vertices such that $e_i$ **is associated with initial vertex $x_{i-1}$ and terminal vertex $x_i$** for $i = 1, \cdots, n$.  
定义：$n$是一个非负整数，$G$是一个**有向图**。$G$中从$u$到$v$的**长度为$n$的path**是一个边的序列$e_1, e_2, \cdots, e_n$，满足存在一个顶点的序列$x_0 = u, x_1, \cdots, x_{n-1}, x_n = v$，使得$e_i$的**initial vertex是$x_{i-1}$，terminal vertex是$x_i$**，$i = 1, \cdots, n$。  

cycle和simple path的定义和无向图中的一样。  

## Connectivity
<!-- An undirected graph is called connected if there is a path between every pair of distinct vertices of the graph.
An undirected graph that is not connected is called disconnected. -->
一个无向图是**connected**的，如果图中任意两个不同的顶点之间都存在一条路径。  
一个不是connected的无向图是**disconnected**的。  

Lemma: 如果图$G$中两个不同的顶点$x$和$y$之间存在一条路径，那么$G$中$x$和$y$之间存在一条simple path。  
Proof: 
删除里面的circuit即可。  
**Theorem**: 一个connected的无向图中任意两个不同的顶点之间都存在一条simple path。  

一个图$G$的**connected component**是一个connected的子图，它不是$G$的另一个connected的子图的proper subgraph。  
也就是说，connected component要满足两个条件：  
- 连通性：它是connected的  
- 最大性：这个子图是最大的连通子图，意味着它不是另一个更大的连通子图的真子图（即，不是另一个连通子图的一部分）  

## Connectedness in Directed Graphs
定义：  
- 一个有向图是**strongly connected**的，如果对于图中的任意两个顶点$a$和$b$，$a$到$b$有一条path，$b$到$a$也有一条path。  
- 一个有向图是**weakly connected**的，如果它的underlying undirected graph是connected的。  
![[assets/Graph_21.png]]  
G是strongly connected的，H是weakly connected的。  

## Cut Vertices and Cut Edges
Sometimes the removal from a graph of a vertex and all incident edges disconnect the graph.
Such vertices are called cut vertices. Similarly we may define cut edges.
有时候，从一个图中删除一个顶点和所有与它关联的边会使得图不再是connected的。这样的顶点被称为**cut vertices**。类似地，我们也可以定义**cut edges**。  
![[assets/Graph_22.png]]  
cut vertices: b, c, e  
cut edges: $\{a, b\}, \{c, d\}$  

一个图$G$的**edge connectivity** $\lambda(G)$是一个edge cut中边的最小条数。  
就是最少需要删除多少条边，才能使得图不再是connected的。这个数值就是edge connectivity。  
![[assets/Graph_23.png]]  
$\lambda(G_1) = 1$; $\lambda(G_2) = 2$; $\lambda(G_3) = 2$; $\lambda(G_4) = 3$  

## Paths and Isomorphism
长度为$k$的simple circuit的存在是isomorphic invariant。这可以用来说明两个图不是isomorphic的。  

### 例1
下面两个图是不是isomorphic的？  
![[assets/Graph_24.png]]  
不是isomorphic的。H有一个长度为3的simple circuit，即$v_1, v_2, v_6, v_1$，而G没有长度为3的simple circuit。  

### 例2
下面两个图是不是isomorphic的？  
![[assets/Graph_25.png]]  
因为很多isomorphic invariants（例如，顶点/边的个数，度数，circuit）都是相同的，所以G和H可能是isomorphic的。  
令$f (u_1) = v_3, f (u_4) = v_2, f (u_3) = v_1, f (u_2) = v_5, f (u_5) = v_4$。我们可以证明$f$是一个isomorphism，所以G和H是isomorphic的。  

### 总结
至此，我们来总结一下几个isomorphic invariants：  
- number of vertices (顶点的个数)  
- number of edges (边的条数)  
- degree sequence (度数序列)  
- existence of simple circuits of various lengths (长度为$k$的simple circuit的存在)  

## Counting Paths between Vertices
Theorem: 假设$G$是一个图，$A$是$G$的adjacency matrix，顶点的顺序是$v_1, v_2, \cdots, v_n$。从$v_i$到$v_j$的长度为$r$的不同的path的个数，其中$r$是一个正整数，等于$A^r$的$(i, j)$位置的值。  

## Euler Paths and Circuits
引入： Ko¨nigsberg seven-bridge problem: 有人想知道是否可以从城镇的某个位置出发，穿过所有的桥一次而不重复，然后回到起点。  

<!-- An Euler circuit in a graph G is a simple circuit containing
every edge of G. An Euler path in G is a simple path containing every
edge of G. -->
定义: 一个图$G$中的**Euler circuit**是一个包含$G$中所有边的simple circuit。一个图$G$中的**Euler path**是一个包含$G$中所有边的simple path。  

### 例1
下面那些有Euler circuit，哪些有Euler path？  
![[assets/Graph_26.png]]  
G1: 有Euler circuit，例如a, e, c, d, e, b, a;  
G2: 既没有Euler circuit，也没有Euler path;  
G3: 有Euler path，例如a, c, d, e, b, d, a, b  

### 例2
下面那些有Euler circuit，哪些有Euler path？  
![[assets/Graph_27.png]]  
<!-- H1: neither; H2: an Euler circuit, e.g., a, g, c, b, g, e, d, f, a; H3: an Euler
path, e.g., c, a, b, c, d, b -->
H1: 既没有Euler circuit，也没有Euler path;  
H2: 有Euler circuit，例如a, g, c, b, g, e, d, f, a;  
H3: 有Euler path，例如c, a, b, c, d, b  

### Necessary Conditions for Euler Circuits and Paths
- Euler Circuit: 每个顶点的度数都是偶数  
- Euler Path: 除了两个顶点的度数是奇数，其他顶点的度数都是偶数。这条path的起点和终点是这两个度数为奇数的顶点。  
**这里书里分了充分条件和必要条件，我不是很明白**  

## Lec 18 P41 看不懂

## Hamilton Paths and Circuits
Euler path是每个边都只经过一次  
**Hamilton path**是每个顶点都只经过一次  

### Necessary Conditions for Hamilton Circuits and Paths
没有已知的充要条件可以判断存在Hamilton circuit或path。  

但是有一些**sufficient conditions**：  
- Dirac’s Theorem: 如果$G$是一个简单图，$\left\vert V \right\vert \geq 3$，并且$G$中每个顶点的度数都大于等于$\frac{\left\vert V \right\vert}{2}$，那么$G$有一个Hamilton circuit。  
- Ore’s Theorem: 如果$G$是一个简单图，$\left\vert V \right\vert \geq 3$，并且对于$G$中的任意两个不相邻的顶点$u$和$v$，$u$和$v$的度数之和都大于等于$\left\vert V \right\vert$，那么$G$有一个Hamilton circuit。  
例子：证明$K_n$有Hamilton circuit  

Hamilton path问题是NP-completez·的

## 最短路劲问题
想必学过ECE220的各位应该都已经知道该用什么算法了  

## Planar Graphs
Definition: A graph is called **planar** if it can be drawn in the **plane without any edges crossing**. Such a drawing is called a **planar representation** of the graph.  
定义：如果一个图可以在平面上画出来，而且没有边相交，那么这个图是**planar**的。这样的画法被称为这个图的**planar representation**。  

例子：$K_4$是planar的吗？  
![[assets/Graph_28.png]]  

关于怎么找planar representation，可以试试先画一个闭合的多边形，然后再把剩下的顶点一个一个加进去  

### Euler's Formula
一个图的planar representation把平面分成了一些区域，包括一个无界区域。
![[assets/Graph_29.png]]  
**Theorem (Euler’s Formula)**: 假设$G$是一个connected的planar simple graph，$e$是边的条数，$v$是顶点的个数，$r$是$G$的planar representation中的区域的个数。那么，$r = e − v + 2$。  

### The Degree of Regions
定义：一个region的**degree**是指这个region的边的条数。当一个边在边界上出现两次的时候，它对degree的贡献是2。  
这句话非常抽象，我们来举两个例子：  
例1： #[Euler's Formula]] 中的图（就是上面那个图），  
degree of region 1 = 3  
degree of region 2 = 3  
degree of region 3 = 3  
degree of region 4 = 3  
degree of region 5 = 3  
degree of region 6 = 7  

例2： 上面那个比较正常，我们看个抽象的：  
![[assets/Graph_30.png]]  
degree of region 1 = 4  
degree of region 2 = 6 (这里bc被计算了两次)  

### Corollaries (推论)
#### Corollary 1
如果$G$是一个connected的planar simple graph，$e$是边的条数，$v$是顶点的个数，$v \geq 3$，那么$e \leq 3v - 6$。  
Proof:  
$$
\begin{aligned}
2e &= \sum_{v\in V}deg(v)\\
& \geq 3r\\
& = 3(e - v + 2)
\end{aligned}
$$
Hence, $e \leq 3v - 6$.

#### Corollary 2
如果$G$是一个connected的planar simple graph，那么$G$有一个顶点的度数不超过5。  
Proof (by contradiction):  
如果$G$有一个或两个顶点，那么结论显然成立。  
如果$G$至少有三个顶点，那么由Corollary 1，$e \leq 3v - 6$。如果$G$中每个顶点的度数都大于5，那么有$2e = \sum_{v\in V}deg(v) \geq 6v$，所以$e \geq 3v$，这与$e \leq 3v - 6$矛盾。  

#### Corollary 3
如果$G$是一个connected的planar simple graph，$e$是边的条数，$v$是顶点的个数，$v \geq 3$，并且$G$中没有长度为3的circuit，那么$e \leq 2v - 4$。  

## Graph Coloring
### Four-color theorem
**Four-color theorem**: 给定一个平面，把它分成一些连续的区域，产生一个叫做map的图形，**最多只需要四种颜色来给map中的区域染色**，使得任意两个相邻的区域的颜色不同。  

### Chromatic number
色数是指给图中的顶点染色，使得相邻的顶点颜色不同，所需的最少颜色数。  
根据Four-color theorem，平面图的色数不超过4。  
记号：$\chi(G)$表示图$G$的色数。  
$K_n$的色数是$n$。
$K_{mn}$的色数是2。
$C_n$的色数是2（当$n$是偶数的时候）或者3（当$n$是奇数的时候）。

## Trees
### Definition
定义：一个**tree**是一个connected的无向图，它没有simple circuit。
**Theorem**: 一个无向图是一个tree，当且仅当它的任意两个顶点之间都有唯一的simple path。
### Rooted Trees
定义：一个**rooted tree**是一个tree，其中一个顶点被指定为root，每条边都是从root指向其他顶点的。
我们可以通过选择任意一个顶点作为root，把一个unrooted tree变成一个rooted tree。
在一个rooted tree中，边的方向可以省略，因为root的选择决定了边的方向。
定义：顶点$v$的**parent**是指唯一的顶点$u$，使得$u$到$v$有一条有向边。
当$u$是$v$的parent的时候，$v$被称为$u$的**child**。
有相同parent的顶点被称为**siblings**。
顶点$v$的**ancestors**是指从root到$v$的路径上的顶点，不包括$v$，包括root。
顶点$v$的**descendants**是指$v$的祖先。
一个rooted tree的顶点被称为**leaf**，如果它没有child。
有child的顶点被称为**internal vertices**。
以$a$为root的**subtree**包括$a$和$a$的descendants，以及所有与这些descendants关联的边。
### m-ary Trees
定义：如果一个rooted tree的每个internal vertex都有不超过$m$个children，那么这个rooted tree被称为**m-ary tree**。如果每个internal vertex都有$m$个children，那么这个rooted tree被称为**full m-ary tree**。特别地，如果$m=2$，那么这个rooted tree被称为**binary tree**。
### Counting Vertices in a Full m-Ary Trees
**Theorem**: 一个有$n$个顶点的tree有$n-1$条边。
**Theorem**: 一个有$i$个internal vertices的full m-ary tree有$n = mi + 1$个顶点。
**Theorem**: 一个有$n$个顶点的full m-ary tree有$i = \frac{n-1}{m}$个internal vertices和$l = \frac{(m-1)n+1}{m}$个leaves。
**Theorem**: 一个有$i$个internal vertices的full m-ary tree有$n = mi + 1$个顶点和$l = (m-1)i + 1$个leaves。
**Theorem**: 一个有$l$个leaves的full m-ary tree有$n = \frac{ml-1}{m-1}$个顶点和$i = \frac{l-1}{m-1}$个internal vertices。
### Level and Height
定义：一个rooted tree中顶点$v$的**level**是指从root到$v$的唯一的path的长度。
一个rooted tree的**height**是指它的顶点的level的最大值。
**Balanced m-ary Trees**: 一个高度为$h$的rooted m-ary tree是**balanced**的，如果所有的leaves都在level $h$或$h-1$。
**Theorem**: 一个高度为$h$的rooted m-ary tree最多有$m^h$个leaves。
**Corollary**: 如果一个高度为$h$的rooted m-ary tree有$l$个leaves，那么$h \geq \lceil \log_m l \rceil$。如果这个m-ary tree是full和balanced的，那么$h = \lceil \log_m l \rceil$。


