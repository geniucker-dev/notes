# Convolution

## 卷积公式怎么来的

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

$$
\begin{aligned}
\int_{-\infty}^{\infty} \mathrm{f}(t)\mathrm{\delta}(t) \, \mathrm{d}t &= \int_{-\infty}^{\infty} \mathrm{f}(0)\mathrm{\delta}(t) \, \mathrm{d}t \\
&= \mathrm{f}(0)\int_{-\infty}^{\infty} \mathrm{\delta}(t) \, \mathrm{d}t \\
&= \mathrm{f}(0)
\end{aligned}$$

$$\int_{-\infty}^{\infty} \mathrm{f}(t)\mathrm{\delta}(t-t_{0}) \, \mathrm{d}t = \mathrm{f}(t_{0})$$

$$
\int_{a}^{b} \mathrm{f}(t)\mathrm{\delta}(t) \, \mathrm{d}t =
\begin{cases}
\mathrm{f}(0) & a<0<b\\
0 & \text{otherwise}
\end{cases}
$$

### Area

$$\int_{-\infty}^{\infty} \mathrm{\delta}(t) \, \mathrm{d}t = 1$$

### Sampling

$$\mathrm{f}(t)\mathrm{\delta}(t) = \mathrm{f}(0)\mathrm{\delta}(t)$$
$$\mathrm{f}(t)\mathrm{\delta}(t-t_{0}) = \mathrm{f}(t_{0})\mathrm{\delta}(t-t_{0})$$

### Scaling

$$\mathrm{\delta}(at) = \frac{1}{\lvert a \rvert }\mathrm{\delta}(t)$$

### Definite Integral

$$
\mathrm{u}(t) = \int_{-\infty}^{t} \mathrm{\delta}(t) \, \mathrm{d}t = 
\begin{cases}
1 & t\geq 0 \\
0 & t<0
\end{cases}
$$

### Unit-step Derivative

$$\frac{\mathrm{d}}{\mathrm{d}t}\mathrm{u}(t) = \mathrm{\delta}(t)$$

### Fourier Transform

$$
\begin{aligned}
\mathrm{F}\{ \mathrm{\delta}(t) \} &= \int_{-\infty}^{\infty} \mathrm{\delta}(t) e^{-j\omega t} \, \mathrm{d}t \\
&= \int_{-\infty}^{\infty} \mathrm{\delta}(t)e^{-j\omega\cdot 0} \, \mathrm{d}t \\
&= 1
\end{aligned}
$$

$$\mathrm{F^{-1}}\{ \mathrm{\delta}(\omega) \} = \frac{1}{2\pi}$$

### Doublet

$$\text{F.D.}\quad \mathrm{F}(\omega)\cdot j\omega\cdot 1 = j\omega \mathrm{F}(\omega)$$
$$\text{T.D.}\quad \mathrm{f}(t)*\mathrm{\delta'}(t) = \mathrm{f'}(t)$$

## Impulse Response

### Fourier transform of power signals

#### Example1: 算$\cos(\omega_{c}t)$的傅里叶变换

$$\cos(\omega_{c}t) = \frac{e^{j\omega_{c}t}+e^{-j\omega_{c}t}}{2}$$

$$\mathcal{F}\{\cos(\omega_{c}t)\} = \frac{\mathcal{F\{e^{j\omega_{c}t}\}}+\mathcal{F}\{e^{-j\omega_{c}t}\}}{2}$$

现在我们来求$\mathcal{F}\{e^{j\omega_{c}t}\}$

我们知道

$$
\begin{aligned}
& \mathrm{f}(t)\leftrightarrow \mathrm{F}(\omega) \\
& \mathrm{f}(t)e^{j\omega_{c}t} \leftrightarrow \mathrm{F}(\omega-\omega_{c}) \\
& \mathrm{\delta}(t) \leftrightarrow 1 \\
& 1 \leftrightarrow 2\pi \mathrm{\delta}(-\omega) = 2\pi \mathrm{\delta}(\omega)
\end{aligned}
$$

所以

$$1 \cdot e^{j\omega_{c}t} \leftrightarrow 2\pi \mathrm{\delta}(\omega-\omega_{c})$$

同理

$$1 \cdot e^{-j\omega_{c}t} \leftrightarrow 2\pi \mathrm{\delta}(\omega+\omega_{c})$$

所以

$$
\begin{aligned}
\mathcal{F}\{\cos(\omega_{c}t)\} &= \frac{1}{2}[2\pi \mathrm{\delta}(\omega-\omega_{c}) + 2\pi \mathrm{\delta}(\omega+\omega_{c})] \\
&= \pi \mathrm{\delta}(\omega-\omega_{c}) + \pi \mathrm{\delta}(\omega+\omega_{c})
\end{aligned}
$$

#### Example2: 算$\mathrm{f}(t)\cos(\omega_{t})$的傅里叶变换

用以下的性质

$$
\begin{aligned}
& \mathrm{f}(t)\cdot \mathrm{g}(t) \leftrightarrow \frac{1}{2\pi}\mathrm{F}(\omega)*\mathrm{G}(\omega) \\
& \mathrm{f}(t)* \mathrm{g}(t) \leftrightarrow \mathrm{F}(\omega)\cdot\mathrm{G}(\omega) \\
\end{aligned}
$$

所以

$$
\begin{aligned}
\mathcal{F}\{\mathrm{f}(t)\cos(\omega_{c}t)\} &= \frac{1}{2\pi} \mathrm{F}(\omega) *[\pi \mathrm{\delta}(\omega-\omega_{c}) + \pi \mathrm{\delta}(\omega+\omega_{c})] \\
&= \frac{1}{2}[\mathrm{F}(\omega-\omega_{c})+\mathrm{F}(\omega+\omega_{c})]
\end{aligned}
$$

#### Example3: 周期信号$\mathrm{f}(t)$的傅里叶变换

$$\mathrm{f}(t) = \sum_{-\infty}^\infty F_{n}e^{jn\omega_{0}t}$$

$$
\begin{aligned}
\mathcal{F}\{\mathrm{f}(t)\} &= \mathcal{F}\left\{  \sum_{-\infty}^\infty F_{n}e^{jn\omega_{0}t}  \right\} \\
&= \sum_{-\infty}^\infty \mathcal{F}\{F_{n}e^{jn\omega_{0}t} \} \\
&= \sum_{-\infty}^\infty 2\pi F_{n} \mathrm{\delta}(\omega-n\omega_{0})
\end{aligned}
$$

#### Example4: 下面这个impuse train的傅里叶变换

$$p(t) = \sum_{-\infty}^\infty \mathrm{\delta}(t-nT)$$

我们先写成傅里叶级数的形式

$$
\begin{aligned}
P_{n} &= \frac{1}{T}\int_{T} p(t)e^{-jn\omega_{o}t} \, \mathrm{d}t \\
&= \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} \mathrm{\delta}(t)e^{-jn\omega_{o}t} \, \mathrm{d}t \\
&= \frac{1}{T}
\end{aligned}
$$

然后根据 Example3

$$P(\omega) = \sum_{n=-\infty}^\infty \frac{2\pi}{T}\mathrm{\delta}\left( \omega-n \frac{2\pi}{T} \right)$$

其中$\omega_{0} = \frac{2\pi}{T}$

### Sampling

考虑下面这个问题：如果对于一个连续函数，我们只有对其进行周期采样的离散值，也就是说，我们只知道

$$f_{n}=\mathrm{f}(nT),\quad -\infty<n<\infty$$

我们能否精确还原原函数？

在一定条件下可以，这里就要提到 Nyquist Sampling Theorem

如果一个函数$\mathrm{f}(t)$为带宽为$B$的带限信号，也就是$\mathrm{f}(t)$不含有频率高于$B$ Hz的成分，或者说傅里叶变换之后$\omega$大于$\Omega_{0}$的时候为0，其中$\Omega_{0}=2\pi B$（如下图）。如果采样周期为$T$，$\frac{1}{T} > 2B$，那么可以还原原信号

![[assets/Pasted image 20240505170501.png]]

下面我们就来说如何还原以及上面的定理为什么正确

令$\mathrm{s}(t) = \mathrm{f}(t)p(t)$，其中$p(t)$是impulse train$p(t) = \sum_{-\infty}^\infty \mathrm{\delta}(t-nT)$

进行傅里叶变换


$$
\begin{aligned}
S(\omega) &= \frac{1}{2\pi} \mathrm{F}(\omega)*P(\omega) \\
&= \frac{1}{2\pi}\mathrm{F}(\omega)*\left[\sum_{n=-\infty}^\infty\frac{2\pi}{T}\mathrm{\delta}\left( \omega-n \frac{2\pi}{T} \right)\right] \\
&= \frac{1}{T} \sum_{-\infty}^\infty \left[ \mathrm{F}(\omega)*\mathrm{\delta}\left( \omega-n \frac{2\pi}{T} \right) \right] \\
&= \frac{1}{T} \sum_{-\infty}^\infty \mathrm{F}\left( \omega-n\omega_{0} \right)
\end{aligned}
$$

![[assets/Pasted image 20240505171319.png | 600]]

接下来我们只需要用$\mathrm{H}(\omega) = T  \mathrm{rect}\left( \frac{\omega}{2\Omega_{0}} \right)$就能得到$\mathrm{F}(\omega)$。但是这里有一个问题，就是可能重叠，如下图，所以我们需要$\omega_{0}-\Omega_{0}>\Omega_{0}\implies \omega_{0}>2\Omega_{0} \implies \frac{1}{T}>2B$

![[assets/Pasted image 20240505171552.png | 600]]

接下来我们来还原原函数

为了得到$\mathrm{F}(\omega)$，我们需要一个$\mathrm{H}(\omega) = T\mathrm{rect}\left( \frac{\omega}{2\Omega_{0}} \right)$

为了方便，我们可以取$2\Omega_{0} = \omega_{o}$

所以$\mathrm{H(\omega)} = T\mathrm{rect}\left( \frac{T\omega}{2\pi} \right)$

根据公式$\mathrm{sinc}(Wt) \leftrightarrow \frac{\pi}{W}\mathrm{rect}\left( \frac{\omega}{2W} \right)$

我们可以得到$\mathrm{h}(t) = \mathrm{sinc}\left( \frac{\pi}{T}t \right)$

所以

$$
\begin{aligned}
\mathrm{f}(t) &= \left( \sum_{n=-\infty}^\infty \mathrm{f}(nT)\mathrm{\delta}(t-nT) \right)*\mathrm{sinc}\left( \frac{\pi}{T}t \right) \\
&= \sum_{n=-\infty}^\infty \mathrm{f}(nT)\mathrm{\delta}(t-nT)*\mathrm{sinc}\left( \frac{\pi}{T}t \right) \\
&= \sum_{n=-\infty}^\infty f_{n} \mathrm{sinc}\left( \frac{\pi}{T}(t-nT) \right)
\end{aligned}
$$
