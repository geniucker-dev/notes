# Convolution

$$\mathrm{f}(t) = \frac{1}{2\pi} \int _{-\infty}^\infty \mathrm{F}(\omega)e^{j\omega t}\mathrm{d}\omega \to \mathrm{y}(t)=\frac{1}{2\pi} \int _{-\infty}^\infty \mathrm{H}(\omega) \mathrm{F}(\omega)e^{j\omega t}\mathrm{d}\omega$$

$$
\begin{aligned}
\mathrm{y}(t) &=
\frac{1}{2\pi} \int _{-\infty}^\infty \mathrm{H}(\omega) \mathrm{F}(\omega)e^{j\omega t}\mathrm{d}\omega \\
&= \frac{1}{2\pi} \int_{-\infty}^\infty \mathrm{H}(\omega) \int_{-\infty}^\infty \mathrm{f}(\tau)e^{-j\omega \tau} \, \mathrm{d}\tau  \, \mathrm{d}\omega \\
&= \int _{-\infty}^\infty \mathrm{f}(\tau) \underbrace{ \frac{1}{2\pi}\int _{-\infty}^\infty \mathrm{H}(\omega)e^{j\omega(t-\tau)} \, \mathrm{d}\omega }_{ \mathrm{h}(t-\tau) }  \, \mathrm{d}\tau
\end{aligned}
$$

$$
\begin{aligned}
\mathrm{y}(t) = \int_{-\infty}^{\infty} \mathrm{f}(\tau)\mathrm{h}(t-\tau) \, \mathrm{d}\tau \triangleq \mathrm{f}(t) * \mathrm{h}(t) & \quad \text{T.D.}\\
\mathrm{Y}(\omega) = \mathrm{F}(\omega)\mathrm{H}(\omega) & \quad \text{F.D.}
\end{aligned}
$$

## 性质

### 交换律 Commutative

$$\mathrm{y}(t)=\mathrm{f}(t)*\mathrm{h}(t)=\mathrm{h}(t)*\mathrm{f}(t)$$

### Time Shift

$$\mathrm{y}(t-t_{0})=\mathrm{f}(t-t_{0})*\mathrm{h}(t)=\mathrm{h}(t-t_{0})*\mathrm{f}(t)$$

### 分配律 Distributive

$$
\begin{aligned}
& \text{T.D.}\quad \mathrm{f}(t)*[\mathrm{g}(t)+\mathrm{h}(t)]=\mathrm{f}(t)*\mathrm{g}(t)+\mathrm{f}(t)*\mathrm{h}(t) \\
& \text{F.D.}\quad \mathrm{F}(\omega)[\mathrm{G}(\omega)+H(\omega)]=\mathrm{F}(\omega)\mathrm{G}(\omega)+\mathrm{F}(\omega)\mathrm{H}(\omega)
\end{aligned}
$$

### Start Point

如果当$t<t_{s,f}时$$\mathrm{f}(t)=0$，当$t<t_{s,h}$时$\mathrm{h}(t)=0$，那么$t<t_{s,f}+t_{s,h}$时$\mathrm{y}(t)=\mathrm{f}(t)*\mathrm{h}(t)=0$

### End Point

如果当$t>t_{e,f}时$$\mathrm{f}(t)=0$，当$t>t_{e,h}$时$\mathrm{h}(t)=0$，那么$t>t_{e,f}+t_{e,h}$时$\mathrm{y}(t)=\mathrm{f}(t)*\mathrm{h}(t)=0$

### Width

如果$\mathrm{f}(t)$的宽度是$T_{f}$，$\mathrm{h}(t)$的宽度是$T_h$，那么$\mathrm{y}(t)=\mathrm{f}(t)*\mathrm{h}(t)$的宽度是$T_{f}+T_{h}$

# Impulse 

## 引入

看一下下面几个例子

$$
\begin{aligned}
& \mathrm{f}(t) + 0 = \mathrm{f}(t) \\
& \mathrm{f}(t) \cdot 1 = \mathrm{f}(t) \\
& \mathrm{f}(t) / 1 = \mathrm{f}(t)
\end{aligned}
$$

上面$0, 0, 1$分别是加法，乘法，除法的单位元，这一节就是找卷积的单位元

$$\mathrm{f}(t)*\mathrm{p}(t) = \mathrm{f}(t) \text{, for all } \mathrm{f}(t)$$

## 定义

$$p_{\epsilon}=\frac{1}{\epsilon}\mathrm{rect}\left( \frac{t}{\epsilon} \right)$$

$$\mathrm{\delta}(t) = \lim_{ \epsilon \to 0 } p_{\epsilon}$$

$\mathrm{\delta}(t)$就是卷积的单位元

## 性质

### Energy

$$
\begin{aligned}
W_{p_{\epsilon}} &= \int_{-\infty}^{\infty} \lvert p_{\epsilon}(t) \rvert^2  \, \mathrm{d}t \\
&= \int_{-\frac{\epsilon}{2}}^{\frac{\epsilon}{2}}\left\lvert  \frac{1}{\epsilon}  \right\rvert^2 \, \mathrm{d}x \\
&= \frac{1}{\epsilon}
\end{aligned}
$$

$$W = \lim_{ \epsilon \to 0 } W_{p_{\epsilon}} = 0$$

### Convolution

$$\mathrm{f}(t)*\mathrm{\delta}(t) = \mathrm{f}(t)$$
$$\mathrm{f}(t)*\mathrm{\delta}(t-t_{0}) = \mathrm{f}(t-t_{0})$$

### Symmetry

$$\mathrm{\delta}(t) = \mathrm{\delta}(-t)$$

### Shifting