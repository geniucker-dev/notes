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

$$\mathrm{y}(t) = \underbrace{ \mathrm{A}(t) }_{ \text{Amplitude} }\cos(\omega_{c}t+\theta_{t})$$