## 回顾

### 从impulse response得到$\mathrm{h}(t)$

$$y(t) = \mathrm{\delta}(t)*\mathrm{h}(t) = \mathrm{h}(t)$$

$$\mathrm{h}(t) = y(t)$$

上式中最右边的$\mathrm{h}(t)$就是impulse response

### 从unit-step response得到$\mathrm{h}(t)$

注意到$\mathrm{\delta}(t) = \frac{\mathrm{d}}{\mathrm{d}t} \mathrm{u}(t)$

$$y(t) = \mathrm{u}(t)*\mathrm{h}(t)$$

所以

$$\frac{\mathrm{d}}{\mathrm{d}t}y(t) = \frac{\mathrm{d}}{\mathrm{d}t}\mathrm{u}(t)*\mathrm{h}(t) = \mathrm{\delta}(t)*\mathrm{h}(t) = \mathrm{h}(t)$$

$$\mathrm{h}(t) = \frac{\mathrm{d}}{\mathrm{d}t}y(t)$$

## Bounded input-bounded output (BIBO) stability

意思是对于任意有界的输入，输出都有界，即如果$\lvert \mathrm{f}(t) \rvert\leq C_{1}<\infty$，则$\lvert y(t) \rvert\leq C_{2}<\infty$

举个例子，如果$\mathrm{h}(t)=\mathrm{u}(t)$，取$\mathrm{f}(t) = \mathrm{u}(t)$，则$y(t) = \begin{cases}0 & t<0 \\ t & t\geq 0\end{cases}$，显然在$t\to +\infty$的时候$\lvert y(t)\rvert\to \infty$。因此，这没有BIBO稳定性

### 定理

如果一个系统是LTI系统，那么这个系统是BIBO当且仅当他的脉冲响应绝对可积，即

$$\int_{-\infty}^{\infty} \lvert \mathrm{h}(t) \rvert  \, \mathrm{d}t < \infty$$

## Causality and LTIC system

定义：如果输出$y(t)$不依赖未来的输入，那么这个系统是causal的

举个例子，如果$y(t)=\mathrm{f}(t+8)$，这里$t$时刻的输出取决于$t+8$时刻的输入，所以他不是causal的

如果输出