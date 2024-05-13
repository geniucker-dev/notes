## 对称矩阵

$$A = A^T$$

对于普通矩阵$A$：$A = S \Lambda S^{-1}$

对于对称矩阵$A$：$A = Q \Lambda Q^{-1} = Q \Lambda Q^{T}$，且有如下性质

1. 特征值是实数
2. 特征向量可以取orthonormal的，在这种情况下$S \to Q$

对于对称矩阵$A$，如果$v_{1}, v_{2}$是两个特征向量，对应特征值$\lambda_{1}, \lambda_{2}$，如果$\lambda_{1}\neq \lambda_{2}$，则$v_{1}\perp v_{2}$

证明：

$$Av_{1} = \lambda_{1} v_{1} \implies v_{1}^{T}A^T = \lambda_{1}v_{1}^T$$

所以

$$v_{1}^{T}A^T v_{2} = \lambda_{1}v_{1}^T v_{2}$$