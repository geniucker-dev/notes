```python
import matplotlib.pyplot as plt
```
## Basic steps
1. Add data.  
2. Plot.
3. Show plot.

## `plt.plot()`
```python
plot([x], y, [fmt])
plot([x], y, [fmt], [x2], y2, [fmt2], ...)
```
The appearance of a line is determined by `color`, `market` and `linestyle`  
The following methods have the identical result:  
```python
plot(x, y, 'go--', linewidth=2, markersize=12)
plot(x, y, color='green', marker='o', linestyle='dashed',
     linewidth=2, markersize=12)
```
- linestyle:
    

