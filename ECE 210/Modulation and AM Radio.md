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

### Coherent demodulation

在接收端，把收到的信号乘$\cos(\omega_{c}t)$

$$
\begin{aligned}
\mathrm{G}(\omega) &= \frac{\mathrm{X}(\omega-\omega_{c}) + \mathrm{X}(\omega+\omega_{c})}{2} \\
&=\frac{\mathrm{X}(\omega-2\omega_{c}) + 2\mathrm{X}(\omega) + \mathrm{X}(\omega+2\omega_{c})}{4}
\end{aligned}
$$

$$$$