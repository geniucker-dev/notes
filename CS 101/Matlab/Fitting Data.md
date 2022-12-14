## Interpolation

## Fit polynomials to data

## Understand limitations of high-order fit

## Distinguish interpolation and fitting (regression)




## Regression/ Curve Fitting
### Interpolation
```MATLAB
x = linspace(0, 1, 11); 
y = x .^ 2;
plot(x, y, 'ro-'); %just for you to see
% Get value of y at x_est
x_est = 0.15;
y_est = interp1(x, y, x_est);
```
[doc](https://ww2.mathworks.cn/help/matlab/ref/interp1.html#btwp6lt-1-method)
### Fitting Polynomials
`polyfit(x, y, n)`
