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

前两个造成了 **整体截断误差（global truncation error）** 

$$E_{n} = \phi(t_{n}) - y_{n}$$

其中$y=\phi(t)$是解，$y_n$是数值解

第三个造成了 **舍入误差（round-off error）**

$$R_{n} = y_{n} - Y_{n}$$

其中$Y_n$是计算机实际上算出来的

那么绝对误差

$$
\begin{aligned}
\lvert \phi(t_{n}) - Y_{n} \rvert &= \lvert \phi(t_{n})-y_{n} + y_{n} - Y_{n} \rvert \\
&\leq \lvert \phi(t_{n})-y_{n} \rvert + \lvert y_{n} - Y_{n} \rvert \\
&= E_{n} + R_{n}
\end{aligned}
$$

### 局部截断误差

$\phi'(t) = \mathrm{f}(t,\phi(t))$

$\phi''(t) = \mathrm{f}_{t}(t,\phi(t))+\mathrm{f}_{y}(t,\phi(t))\mathrm{f}(t,\phi(t))$

然后我们使用泰勒级数在$t_{n}$处展开$\phi$

$\phi(t_{n}+h) = \phi(t_{n}) + \phi'(t_{n})h + \frac{1}{2}\phi''(\bar{t_{n}})h^2$

其中$\bar{t_{n}}$是$t_{n}<\bar{t_{n}}<t_{n}+h$的某一点

进行带入，我们得到

$\phi(t_{n+1}) = \phi(t_{n}) + h\mathrm{f}(t_{n},\phi(t_{n})) + \frac{1}{2}\phi''(\bar{t_{n}})h^2$

所以

$y_{n+1}^* = \phi(t_{n}) + h\mathrm{f}(t_{n},\phi(t_{n}))$

所以上面欧拉法的局部误差项就是

$e_{n+1} = \phi(t_{n+1}) - y_{n+1}^*=\frac{1}{2}\phi''(\bar{t_{n}})h^2$

$\lvert e_{n+1} \rvert \leq \frac{1}{2}Mh^2$

其中$M$是$\lvert \phi''(\bar{t_{n}}) \rvert$在区间$[a,b]$上的最大值

**全局截断误差**

$$\lvert E_{n} \rvert \leq Kh$$

所以欧拉法是一种 **first-order method**