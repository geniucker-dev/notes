### to Solve a polynomial
MATLAB represents polynomials as row vectors of coefficients starting from the ***highest-order term to the lowest***.
e.g. 
$x^2-4$ is represented as `[1 0 -4]`
$3x^3+x^2-4$ is represented as `[3 1 0 -4]`
Thus a polynomial is a length (n + 1) array.

- `polyval`: e.g. `polyval([1 0 4], 2)` will evaluate the value of $x^2-4$ when $x=2$
- `conv`: multiply polynomials:
    ```MATLAB
    u = [3 0 -1];
    v = [2 5];
    w = conv(u, v);
    ```
- `roots`: get the roots of polynomials. e.g. `roots([1 0 -4])`
- `poly`: to get an equation from the roots you given.
    e.g.
    ```MATLAB
    poly([-2 2])  % [1 0 -4]
    ```

### Find function zeros not just polynomials
$cosx=e^{-x}-4$
```MATLAB
f = @(X) cos(x)-exp(-x)+4;
x = fzero(f, x0);  % finds a zero of f near x0
```