对于$\frac{\mathrm{d}y}{\mathrm{d}t} = \mathrm{f}(t,y)$以及初始条件$y(t_{0})=y_{0}$

$\frac{\mathrm{d}\phi}{\mathrm{d}t}(t_{n})=\mathrm{f}(t_{n},\phi(t_{n}))$

我们有近似：$\frac{\phi(t_{n+1}-t_{n})}{t_{n+1}-t_{n}}\cong\mathrm{f}(t_{n},\phi(t_{n}))$

所以可以得到迭代式：$y_{n+1} = y_{n} + \mathrm{f}(t_{n},y_{n})(t_{n+1}-t_{n})$

如果对于任意n，$t_{n+1}-t_{n}=h$是定值，我们把$\mathrm{f}(t_{n},y_{n})$表示为$f_{n}$，那么上面的式子可以表示为

$$y_{n+1} = y_{n} + hf_{n}$$

### 流程

1. 定义$\mathrm{f}(t,y)$
2. 输入初始值$(t,y)=(t_{0},y_{0})$
3. 输入步长 $h$ 以及步数 $n$
4. 输出 $t_{0}$ 和 $y_{0}$
5. for j from 1 to n do
6. $f_{n} = \mathrm{f}(t,y)$  
    $y = y + h*f_{n}$
    $t = t + h$
7. 输出 $t$ 和 $y$
8. 结束

## 反向欧拉

$$y_{n+1} = y_{n} + h\mathrm{f}(t_{n+1},y_{n+1})$$

我们可以得到下面的式子（课本里没说这个，只说了上面的是implicit Euler formula）

$$y_{n} = y_{n+1} - h\mathrm{f}(t_{n+1},y_{n+1})$$

## 误差

### 误差来源

1. 迭代式本身就是个近似
2. 除了第一步以外，输入数据只是真实值的近似
3. 计算机精度

