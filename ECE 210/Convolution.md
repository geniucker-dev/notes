$$\mathrm{f}(t) = \frac{1}{2\pi} \int _{-\infty}^\infty \mathrm{F}(\omega)e^{j\omega t}\mathrm{d}\omega \to \mathrm{y}(t)=\frac{1}{2\pi} \int _{-\infty}^\infty \mathrm{H}(\omega) \mathrm{F}(\omega)e^{j\omega t}\mathrm{d}\omega$$

$$
\begin{aligned}
\mathrm{r}(t) &=
\frac{1}{2\pi} \int _{-\infty}^\infty \mathrm{H}(\omega) \mathrm{F}(\omega)e^{j\omega t}\mathrm{d}\omega \\
&= \frac{1}{2\pi} \int_{-\infty}^\infty \mathrm{H}(\omega) \int_{-\infty}^\infty \mathrm{f}(\tau)e^{-j\omega \tau} \, \mathrm{d}\tau  \, \mathrm{d}\omega \\
&= \int _{-\infty}^\infty \mathrm{f}(\tau) \frac{1}{2\pi}\int _{-\infty}^\infty \mathrm{H}(\omega)e^{j\omega(t-\tau)} \, \mathrm{d}\omega  \, \mathrm{d}\tau 
\end{aligned}
$$