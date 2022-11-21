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

## Brute-Force Optimization
Two useful functions from the `itertools` module:
- `itertools.combinations(iterable, r)`: can provide all subsets of size n.  
    [doc](https://docs.python.org/3/library/itertools.html#itertools.combinations)
    ```python
    >>> list(combinations([1,2,3],0))
    [()]
    >>> list(combinations([1,2,3],1))
    [(1,), (2,), (3,)]
    >>> list(combinations([1,2,3],2))
    [(1, 2), (1, 3), (2, 3)]
    >>> list(combinations([1,2,3],3))
    [(1, 2, 3)]
    >>> list(combinations([1,2,3],4))
    []
    ```
- `itertools.product(*iterables, repeat=1)`: can replace nested for loops.  
    [doc](https://docs.python.org/3/library/itertools.html#itertools.product)
    ```python
    >>> list(product(range(2),range(3)))
    [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2)]
    >>> list(product(range(2), 2))  # same as list(product(range(2), range(2)))
    [(0, 0), (0, 1), (1, 0), (1, 1)]
    ```
## Heuristic optimization
Heuristic algorithms don’t guarantee the ‘best’ solution, but are often adequate (and the only choice!)\*.
> Figure of merit: A figure of merit is to classify how good the solutions are. A figure of merit is normally a value to classify candidate solutions by how good they are. Some textbooks also define figure of merit as a function/equation. It is like exam02, the exam mark is the figure of merit you use to see if you are a good, very good, very very good …. very very very x 1000 good student.  
### Hill-climbing algorithm
Steps:  
1. Create a formula to calculate the **figure of merit**, f. Something that can be used to compare.  
2. Select a starting **guess**, $x_0$.  
3. Change a part of the **guess**.  
4. If this improves, keep it and repeat C.  
5. If no improvement is possible, terminate.