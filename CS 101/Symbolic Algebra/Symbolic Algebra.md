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

## Math functions
- Complex number
    - `sympy.I` is `sqrt(-1)` is `j` in python’s complex number
    - `sympy.re(xxxx)`
    - `sympy.im(xxxx)`
- `sympy.pi`
- `sympy.E`: same as `sympy.exp(1)`
- `sympy.exp()`
- `sympy.sqrt()`
- ...

## Polynomials and expressions
- `expr.subs(a, 1)`: return the result that substitutes a with 1
- `sympy.expand((x+1)*(x-1))`: `x**2 - 1`
- `sympy.factor(x**2 + 4*x + 4)`: `(x + 2)**2`
- `sympy.simplify(eqn)`: simplify the equation
- `sympy.together(b/c + x/a)`: `(a*b + c*x)/(a*c)`
- `sympy.apart((a*x)/((a-2)*b),a)`: `x/b + 2*x/(b*(a - 2))`
    `sympy.apart((a*x)/((a-2)*b),b)`: `a*x/(b*(a - 2))`
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
sympy.plotting.plot3d_parametric_surface(expr_x, expr_y, expr_z, range)
```

## Calculus
### Symbolic differentiation
```python
x, n = sympy.S('x, n')
sympy.diff(x**n, x, 1)  # equals to sympy.diff(x**n, x)
# 1 refers to the time you want to diff
```
### Symbolic integration
#### Indefinite integration
`sympy.integrate()` does not show the integration constant, `C`  
e.g.
`sympy.integrate(x**2, x)`: `x**3/3`  
#### Definite
e.g.
`sympy.integrate(sympy.cos(x), (x, 0, sympy.pi/2))`: `1`
$$\int^1_0dy\int^1_{-1}dx(sin^2x+3y)$$
=>
```python
sympy.integrate(sympy.integrate(sympy.sin(x)**2 + 3*y, (x, -1, 1)), (y, 0, 1))
```
### Taylor series & Linearization
`sympy.series(expr, x, x0=0, n=6)`
***attention:*** `n` is the number of terms in Taylor series, not the number of terms you can see (就是展开到泰勒的第几项)
e.g.
```python
sympy.series(1/(1-x), x, 0)
# 1 + x + x**2 + x**3 + x**4 + x**5 + O(x**6)
```
```python
# we can use .removeO() to remove O
sympy.series(1/(1-x), x, 0).removeO()
# x**5 + x**4 + x**3 + x**2 + x + 1
```
```python
sympy.series(sympy.cos(x), x, 0, 3).removeO()
# 1 - x**2/2
sympy.series(sympy.cos(x), x, 0, 4).removeO()
# 1 - x**2/2
sympy.series(sympy.cos(x), x, 0, 5).removeO()
x**4/24 - x**2/2 + 1
```

## `lambdify`
`lambdify` can turn a `sympy` expression into a lambda function
`lambdify([parameters], expr)`: if there's only one parameter in expr, the first parameter in lambdify doesn't need to be a list  
e.g.
```python
f = lambdify([x], x+1)
# equals to f = lambdify(x, x+1)
# it can be called like f(10)
```
```python
f = lambdify([x, y], x+y)
# it can be called like f(1, 2)
```