```python
import sympy as sy
```
`sympy` provides symbolic and related mathematical functions.  
Steps:
Define variable: `x = sy.S('x')  # or sy.Symbol('x')`  

### Solving equation analytically
#### a
1. `a, b, c, x = sympy.S('a, b, c, x')`  
2. `eqn = a*x**2 + b*x + c`  
3. `y = sympy.solve(eqn, x)`  
4. `print(y)`  
- The answer is stored in a container data type so the output will be `[(-b - sqrt(-4*a*c + b**2))/(2*a), (-b + sqrt(-4*a*c + b**2))/(2*a)]`  
- To get value of `y` for `a=1, b=2, c=1`  
    use:
    ```python
    print(y[0].subs(a, 1).subs(b, 2),subs(c, 1))  # -1
    ```

> If the equation can't be solved by any technique known to sympy, it will return a empty list.

e.g.  
```python
print(sympy.solve(a*x**5 + b*x + c, x))  # []
```

#### b
```python
import sympy as sy
x, y = sy.S('x, y')
eq1 = x + y - 6
eq2 = -y + x + 4
z = sy.solve((eq1, eq2), (x, y))
```
the value of `z`: `{x: 1, y: 5}`

## Polynomials and expressions
- `sympy.expand((x+1)*(x-1))`: `x**2 - 1`
- `sympy.factor(x**2 + 4*x + 4)`: `(x+2)**2`
- `sympy.simplify(eqn)`: simplify the equation