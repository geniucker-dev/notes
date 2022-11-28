```python
import sympy
# or
import sympy as sy
```
`sympy` provides symbolic and related mathematical functions.  
Steps:
Define variable: `x = sy.S('x')  # or sy.Symbol('x')`  

## Solving equation analytically
### single equation
```python
a, b, c, x = sympy.S('a, b, c, x')
eqn = a*x**2 + b*x + c
y = sympy.solve(eqn, x)
print(y)
# [(-b - sqrt(-4*a*c + b**2))/(2*a), (-b + sqrt(-4*a*c + b**2))/(2*a)]
```
- The answer is stored in a container data type
- To get value of `y` for `a=1, b=2, c=1`  
    use:
    ```python
    print(y[0].subs(a, 1).subs(b, 2),subs(c, 1))
    # -1
    ```

> If the equation can't be solved by any technique known to sympy, it will return a empty list.

e.g.  
```python
print(sympy.solve(a*x**5 + b*x + c, x))
# []
```

### equation set
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
- `sympy.together(b/c + x/a)`: `(a*b + c*x)/(a*c)`
**attention**:
```python
sympy.simplify(sympy.sin(x)**2 + sympy.cos(x)**2)
# 1
sympy.simplify(math.sin(x)+math.cos(x))
# error, because you use math rather than sympy
sympy.expand((sympy.cos(x)+sympy.sin(x))**2)
# sin(x)**2 + 2*sin(x)*cos(x) + cos(x)**2
```

## Plotting
### 2-D
`Sympy` can also plot expressions
```python
sympy.plotting.plot(x**2)
sympy.plotting.plot(x**2, (x, -2, 2))  # this limits the -2<=x<=2
sympy.plotting.plot( (sin(x),(x, -2*pi, 2*pi)),(cos(x), (x, -pi, pi)), line_color='red', title='SymPy plot example')  # multiple lines
```
![[three_dimensional_plot.jpg|300]]
### 3-D
```python
sympy.plotting.plot3d(sympy.cos(x) * sympy.sin(y))
```
parametric line or surface (optional)
```python
sympy.plotting.plot3d_parametric_line(expr_x, expr_y, expr_z, range)
```