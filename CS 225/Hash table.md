A hash function consists of:

1. hash function $h(k)$
2. array
3. collision resolution strategies

SUHA: Simple Uniform Hashing Assumption，意思大概是均匀分布，定义为$\mathrm{P}(\mathrm{h}(a)=\mathrm{h}(b))=\frac{1}{m}$

一个好的哈希函数满足：
- 常数时间（$\mathrm{O}(1)$）
- 确定性（如果$k_1==k_2 \implies h(k_1)==h(k_2)$

## Collision Handlin

### Separate Chaining

使用链表来存储

假设 $S = \{ 16, 8, 4, 13, 29, 11, 22 \}$, $h(k) = k \% 7$

![[assets/Pasted image 20240410091435.png | 400]]

load factor $\alpha = \frac{n}{N}$

注意到会有空位没用（unbounded），所以这是一个 open hashing

### Probe-based Hashing

假设 $S = \{ 16, 8, 4, 13, 29, 11, 22 \}$, $h(k) = k \% 7$

![[assets/Pasted image 20240410093044.png | 500]]

缺点：即使负载低也很容易拥挤，导致寻址变慢

## Double Hashing

![[assets/Pasted image 20240419142315.png | 500]]

## 时间 （不用记）

下面是SUHA条件下找到一个key的期望寻找次数

### Linear Probing

- Successful: $\frac{1}{2}\left( 1+\frac{1}{1-\alpha} \right)$
- Unsuccessful: $\frac{1}{2}\left( 1+\frac{1}{1-\alpha} \right)^2$

### Double Hashing

- Successful: $\frac{1}{\alpha} \times \ln\left( \frac{1}{1-\alpha} \right)$
- Unsuccessful: $\frac{1}{1-\alpha}$

### Separate Chaining

- Successful: $1+\frac{\alpha}{2}$
- Unsuccessful: $1+\alpha$

## 重哈希

从上面知道，$\alpha$大的时候哈希表会速度会退化，所以在$\alpha$达到一定值我们需要进行重哈希。

我们一般吧哈希表大小扩大到原来的2倍，然后重新进行哈希映射

## 复杂度

### 时间复杂度
- 查找：
    - 平均：$\mathrm{O}(1)$
    - 最差：$\mathrm{O}(n)$
- 插入：
    - 平均：$\mathrm{O}(1)$
    - 最差：$\mathrm{O}(n)$

### 空间复杂度

$\mathrm{O}(n)$

$N \approx 1.5n$

## 几个std ADS

### std::map

是红黑树实现的

方法：
- `operator[]`
- `insert`
- `erase`
- `lower_bound(key)`
- `upper_bound(key)`