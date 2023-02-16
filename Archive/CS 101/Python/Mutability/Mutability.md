## Mutability and immutability
- **Immutability** describes objects with values that are **not changeable** in memory.  
    Basic Python data types - `str`, `int`, `float`, `complex` are **immutable**  
    e.g. 
    ```python
    x = 3.141
    y = x
    
    y = 4.0
    ```
    ![[Immutability.excalidraw]]
- **Mutability** describes values that are **changeable** in memory, often when values share the same location.
    python types `list` and `dict` are mutable  
    e.g.
    ```python
    x = [1, 2, 'a']
    y = x
    
    y[2] = 3
    ```
    ![[Mutability.excalidraw]]

    > Aliasing occurs when **one memory location has two names**.
    > ***Aliasing causes mutable types to behave unexpectedly!***

As for `list`, if you want to avoid the unexpected behavior, you can use a copy of it.  
e.g.  
```python
a = [1, 2, 3]
b = a[:]  ## or b = a.copy()
```
# ***Don't Forget `dict` and `list` are mutable while reading codes!!!***