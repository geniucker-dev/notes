## Equations
### How do we represent equations on computers?
- As a function  
- write some expressions  
- write as series (or we can say we represent an equation as a pair of arrays, `x` and `y`)  
- We can also represent equations using symbols from the library `sympy` (later lectures).
### How to quantify who is more efficient?
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

## Solve an equation
- Use graph  
- *Newton's Method*
    In conclusion, the iterative formular is: $x_n = x_{n-1} - \frac{x_{n-1}}{f'(x_{n-1})}$
    In python, we can use `scipy.optimize.newton(f, x0)`

## Optimize
### Finding minimum of y
```python
import scipy.optimize
```
we can find minima using:
- `scipy.optimize.fmin(f, x0)` [doc](https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.fmin.html)
    It will return an `ndarray` of optimized `x`, ***NOT f***
- `scipy.optimize.minimize(f,x0)`
    It will return an object containing lots of information
    e.g.
```python
def f(x):
    return x**2
result = scipy.optimize.minimize(f, x0=2)
print(result)
```
It will print:
```
      fun: 3.5662963072207506e-16
 hess_inv: array([[0.5]])
      jac: array([-2.2868119e-08])
  message: 'Optimization terminated successfully.'
     nfev: 6
      nit: 2
     njev: 3
   status: 0
  success: True
        x: array([-1.88846401e-08])
```
If you want to get the optimized `x`, you can use `result.x`, others are similar.
### Finding maxima of y
You can find the minima of $-y$