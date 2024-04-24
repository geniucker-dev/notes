### Frequency shift
$$\mathrm{f}(t)\leftrightarrow \mathrm{F}(\omega)$$

$$\mathrm{g}(t)=\mathrm{f}(t)e^{j \omega_{c}t} \leftrightarrow  \mathrm{G}(\omega)=\mathrm{F}(\omega-\omega_{c})$$

![[assets/Pasted image 20240423142913.png | 800]]

### Modulation

$$\mathrm{f}(t)\leftrightarrow \mathrm{F}(\omega)$$

$$\mathrm{x}(t) = \mathrm{f}(t)\cos(\omega_{c}t)$$

$$
\begin{aligned}
\mathrm{x}(t) &= \mathrm{f}(t)\cos(\omega_{c}t) \\
&= \mathrm{f}(t) \frac{e^{j\omega_{c}t} - e^{-j\omega_{c}t}}{2}
\end{aligned}
$$

Hence,

$$\mathrm{X}(\omega) = \frac{\mathrm{F}(\omega-\omega_{c}) + \mathrm{F}(\omega+\omega_{c})}{2}$$

![[assets/Pasted image 20240423143400.png | 800]]

![[assets/Pasted image 20240423143553.png | 800]]

$$\mathrm{y}(t) = \underbrace{ \mathrm{A}(t) }_{ \text{amplitude} }\cos(\underbrace{ \omega_{c} }_{ \text{frequency} }t+\underbrace{ \theta_{t} }_{ \text{phase} })$$

## 为什么调制

### 天线长度

信号的波长：$\lambda = \frac{c}{f_{c}}$

有效传输的天线长度：$L > \frac{\lambda}{4}=\frac{c}{4f_{c}}$

几种常见的波对应的天线长度：

- 声波波长$\approx 15 \text{KHz} \implies L>5 \text{Km}$
- AM: $580\text{KHz} \implies L>130 \text{m}$
- FM: $100\text{MHz} \implies L>75 \text{cm}$
- 卫星：$10\text{GHz} \implies L>7.5 \text{mm}$

### 可用带宽

不可能全部在基带发送，因为发射机的频率是固定的

## AM解调

如上面所说，发送端发送信号$\mathrm{x}(t)=\mathrm{f}(t)\cos(\omega_{c}t)$，$\mathrm{X}(\omega)=\frac{\mathrm{F}(\omega-\omega_{c}) + \mathrm{F}(\omega+\omega_{c})}{2}$

### 相干解调 Coherent demodulation

在接收端，把收到的信号乘$\cos(\omega_{c}t)$

$$
\begin{aligned}
\mathrm{G}(\omega) &= \frac{\mathrm{X}(\omega-\omega_{c}) + \mathrm{X}(\omega+\omega_{c})}{2} \\
&=\frac{\mathrm{X}(\omega-2\omega_{c}) + 2\mathrm{X}(\omega) + \mathrm{X}(\omega+2\omega_{c})}{4}
\end{aligned}
$$

![[assets/Pasted image 20240423162900.png | 600]]

然后我们再加个Low Pass Filter就能把中间的滤出来

如果信道不是理想的，即$\mathrm{g}(t)=\mathrm{x}(t-t_{0})\cos(\omega_{c}t)$

$$
\begin{aligned}
\mathrm{g}(t) &= \mathrm{x}(t-t_{0})\cos(\omega_{c}t) \\
&= \mathrm{f}(t-t_{0})\cos[\omega_{c}(t-t_{0})]\cos(\omega_{c}t) \\
&= \mathrm{f}(t-t_{0})\left[ \frac{1}{2}\cos[2\omega_{c}t-\omega_{c}t_{0}]+\frac{1}{2}\cos(\omega_{c}t_{0}) \right] \\
&= \underbrace{ \frac{1}{2}\mathrm{f}(t-t_{0})\cos(2\omega_{c}t-\omega_{c}t_{0}) }_{ \text{blocked} }+\underbrace{ \frac{1}{2}\mathrm{f(t-t_{0})}\cos(\omega_{c}t_{0}) }_{ \text{pass through LPF} }
\end{aligned}
$$

**要相位同步？？？**

### 包络检测 Envelop Detection

$$
\begin{aligned}
\lvert \mathrm{x}(t) \rvert &=
\lvert \mathrm{f}(t)\cos(\omega_{c}t) \rvert \\
&= \mathrm{f}(t) \lvert \cos(\omega_{c}t) \rvert \\
&= \mathrm{f}(t) \left[ \sum_{n=1}^\infty c_{n}\cos(2n\omega_{c}t+\theta_{n}) \right] \\
&= \frac{c_{0}}{2}\mathrm{f(t)} + \sum_{n=1}^\infty \mathrm{f}(t) c_{n} \cos(2n\omega_{c}t+\theta_{n})
\end{aligned}
$$

对上面这玩意儿进行傅里叶变换

$$
\mathrm{X}(\omega) = \frac{c_{0}}{2}\mathrm{F}(\omega) + \sum_{n=1}^\infty \frac{c_{n}}{2}\left[ \mathrm{F}(\omega-2n\omega_{c})e^{j\theta n} + \mathrm{F}(\omega+2n\omega_{c})e^{-j\theta n} \right]
$$

![[assets/Pasted image 20240424122719.png | 800]]

用低通即可分离出原始信号

在上面的计算里我们假设了$\mathrm{f}(t)>0$，如果遇到信号小于0，可以先加上一个直流偏移量$D$，包络检测之后再减去$D$

![[assets/Pasted image 20240424122937.png | 800]]

