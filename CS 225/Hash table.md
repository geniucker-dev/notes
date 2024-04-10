A hash function consists of:

1. hash function $h(k)$
2. array
3. collision resolution strategies

## Collision Handling

### Separate Chaining

使用链表来存储

假设 $S = \{ 16, 8, 4, 13, 29, 11, 22 \}$, $h(k) = k \% 7$

![[assets/Pasted image 20240410091435.png | 400]]

load factor $\alpha = \frac{n}{N}$
### Probe-based Hashing

