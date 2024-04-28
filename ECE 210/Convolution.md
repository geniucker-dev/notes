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

    