## 回顾一下MATH234

差不多就是每个元素只在一个子集里面

![[assets/Pasted image 20240422092259.png]]

`find(0)==find(1)`

## 数据结构

在数据结构中，为了方便表示，对于每一个子集我们用一个代表元素（representive element）来表示

- 维护一个集合 $S=\{ S_{0}, S_{1}, \dots, s_{k} \}$
- 每个子集都有一个代表元素（representive element）
- 接口：
    - `void makeset(const T& t);`
    - `void union(const T& k1, const T& k2);`
    - `T& find(const T& k);`

## 实现

我们用一个树状结构来表示