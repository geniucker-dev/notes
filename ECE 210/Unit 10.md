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