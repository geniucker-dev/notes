```python
import numpy as np
```

### Create an array
- `np.array(object, dtype=None)`
    it will return an array object whose type is `ndarray`  
    `object` can be an array like object like `list`, or can be a scalar. If it's a scalar, it will return a 0-dimensional array. The shape will be `()`, which will be detailed later.  
- `np.zeros(shape, dtype=float)`: return a new array of given shape and type, filled with zeros. The default of `dtype` is `np.float64`  
    If `shape` is scalar, it'll return a 1-D array.  
- `np.ones(shape, dtype=float)`: similar to `np.zeros()` but filled with ones.  
- `np.eye(N, M=None, dtype=float)`: return a 2-D array with ones on the diagonal and zeros elsewhere.
    `N`: number of rows  
    `M`: numbers of columns. If None, defaults to `N`

### Property, methods and operators of ndarray
[doc](https://numpy.org/doc/stable/reference/generated/numpy.ndarray.html)
- `ndarray[row][col]` or `ndarray[row, col]`  
- some strange usages of slice  
    e.g.  
    ```python
    a = np.array([[1, 2, 3],
                  [4, 5, 6],
                  [7, 8, 9]])
    a[0:100, 0]   # 1 notice 100 is out of index but it's valid
    a[[0, 2], :]  # 2
    a[[0, 2]]     # 3 same as # 2
    ```
    the code above is valid
- `ndarray.shape` or `np.shape(ndarray)`:  
    1-D array: `np.array([4.5, 6.0, 1.2, 5.4]).shape` => `(4,)`  
    2-D array: `np.array([[4.5, 6.0, 1.2, 5.4]]).shape` => `(1, 4)`  
    scalar (0-D): `np.array(4.5).shape` => `()`  
- `ndarray.dtype`: return the `dtype` of the array  
- `ndarray.T`: return the transposed array  
- `ndarray * ndarray`: multiply element-wise  
    e.g.  
    ```python
    x = array([[1, 2], [3, 4]])
    print(x * x)
    ```
    will be `array([[1, 4], [9, 16]])`
- `ndarray.tolist()`: convert `ndarray` to a python `list`
- `ndarray.sort(axis=-1)`: it will change the value of `ndarray` and won't return  
    `axis` is axis along which to sort. Default is `-1`, which means sort along the last axis.  
    e.g.
    ![[Array.excalidraw]]
- `ndarray.argsort(axis=-1)`: returns the indices that would sort this array. `axis` is the same as that in `ndarray.sort()`  
    e.g.
    ```python
    x = array([[2, 54, 3], [6, 45, 1]])
    print(x.argsort())
    ```
    will be:
    ```
    [[0 2 1]
     [2 0 1]]
    ```
- `ndarray.max(axis=None)`: return the maximum along a given axis. If `None`, return the max of the whole array  
- `ndarray.min(axis=None)`: similar to `ndarray.max()`  
- `ndarray.mean(axis=None)`: similar to `ndarray.max()`  
- `ndarray.sum(axis=None)`: `True` can be considered as `1` and `False` as `0`  

### `linspace`
[doc](https://numpy.org/doc/stable/reference/generated/numpy.linspace.html)
`np.linspace(start, stop, num=50, endpoint=True)`

### Comparing numpy arrays
- `ndarray.all()`: Returns True if all elements evaluate to True, similar to `np.all(a)` (`a` is array-like object)  
- `ndarray.any()`