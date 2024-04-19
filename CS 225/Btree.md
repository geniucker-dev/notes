一个$m$阶B树的性质：
- 一个node内的key是有序的
- 一个node包含至多$m-1$个keys
- 内部node到child个数等于key个数+1
- 根节点可以是叶节点或者有$\left[ 2, m \right]$个孩子
- 一个非根内部节点有$\left[ \mathrm{ceil}(m/2), m \right]$个孩子
- 所有叶节点在同一层

一个m阶高度为h的B树最少节点：$2t^h-1$，其中$h=\mathrm{ceil}(m/2)$