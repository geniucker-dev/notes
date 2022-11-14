## How do we represent equations on computers?
- As a function  
- write some expressions  
- write as series (or we can say we represent an equation as a pair of arrays, `x` and `y`)  
- We can also represent equations using symbols from the library `sympy` (later lectures).
## How to quantify who is more efficient?
***`timeit`***
- not in jupyter: 
```python
import timeit
code = "for i in range(100): pass"
xx = timeit.timeit(code, numbers=1000000)  # the default value of numbers is 1000000
```
    or
```python
import timeit
def yourFunc():  # your own function
    pass
xx = timeit.timeit(yourFunc)
```
- in jupyter notebook:
```python
import timeit
%timeit myCode(argument)  #this is one easy way to run in Jupyter
# myCode is just your function name
```