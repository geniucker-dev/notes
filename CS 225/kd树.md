## 基本操作

### 构建

每一层根据不同维度划分子树

举个例子，一个三维的点，根节点根据第0维，第一层根据第1维分，第二层根据第2维分，第三层根据第0维分...

### 插入

和BST一样，只是每一层划分依据是其中一个维度

### 删除

好像没教

## 最近邻搜索

1. 先递归二叉搜索到叶节点，存为最近邻
2. 回溯到倒数第二层，判断根节点是否是否更近，若是，更新最近邻
3. 如果被查询点到当前最近邻的距离大于等于当前根节点到当前判断维度的距离，那么往另一个子树搜索（就是以被查询点为球心，被查询点到当前最近邻的距离为半径的超球体和当前判断维度的超平面是否相交，相交就要搜索另一子树）
4. 直到回溯到根节点