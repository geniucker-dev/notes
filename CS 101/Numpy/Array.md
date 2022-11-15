```python
import numpy as np
```

### Create an array
```python
np.array(object, dtype=None)
```
it will return an array object whose type is `ndarray`
`object` can be an array like object like `list`, or can be a scalar. If it's a scalar, it will return a 0-dimensional array. The shape will be `()`, which will be detailed later.

### Property, methods and operators
- `ndarray.shape` or `np.shape(ndarray)`:
    1-D array: `np.array([4.5, 6.0, 1.2, 5.4]).shape` => `(4,)`
    2-D array: `np.array([[4.5, 6.0, 1.2, 5.4]]).shape` => `(1, 4)`
    scalar (0-D): `np.array(4.5).shape` => `()`
- `ndarray.dtype`: 
- `ndarray[row][col]` or `ndarray[row, col]