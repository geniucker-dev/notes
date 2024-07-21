## 正交向量

### 向量的长度

$v = (v_{1}, v_{2},\cdots, v_{n})$

Then $\lvert v \rvert = \sqrt{ v_{1}^2 + v_{2}^2 + \cdots + v_{n}^2 } = \sqrt{ v^{\mathrm{T}}v }\geq 0$

### 向量内积

$v^\mathrm{T} w = \sum_{i}v_{i}w_{i} = \lvert v \rvert \lvert w \rvert \cos(\theta)$

$\cos(\theta) = \frac{v^\mathrm{T}w}{\lvert v \rvert\lvert w \rvert}$, $-\frac{\pi}{2} \leq \theta \leq \frac{\pi}{2}$

### 正交向量

$\theta=\frac{\pi}{2} \text{ or } -\frac{\pi}{2}$

$\cos(\theta)=0$

$v^\mathrm{T}w = 0$

## 正交子空间

### 定义

定义：有两个子空间$V$，$W$，如果对于$\forall v \in V, \forall w \in W,  v^\mathrm{T}w=0$，那么$V \perp W$
