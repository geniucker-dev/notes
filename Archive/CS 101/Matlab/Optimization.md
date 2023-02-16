### Minimize
```MATLAB
x = -1:.01:2;
y = humps( x );
Optimize/Solving
% a function available in MATLAB
xstar = fminbnd( @humps,0.3,1 )
% or
[xstar, ystar ] = fminbnd( @humps,0.3,1 )
figure 
plot( x, y, xstar, ystar, 'ro' )
xlabel( 'x' ) 
ylabel( 'f(x)' ) 
grid on
```

the `@`sign
```MATLAB
y = humps( x ); % a matlab or your func in .m file 
xstar = fminbnd( @humps, 0.3, 1 )
```
and
```MATLAB
f = @(x) cos(x) - exp(-x) + 4 % inline func
xstar = fminbnd( f, 0.3, 1 )
```
Use @ when your function is not defined 
in the same code.

### Numerical Integration
e.g.
```MATLAB
x = linspace( 0,10,11 );
y = [ 0.11 0.09 0.09 0.10 0.11 0.11 0.09 0.10 0.08 0.09 0.11 ];
```
when we don't know the equation, we can `trapz` to calculate the area of a given data sets.
```MATLAB
integral = trapz( x,y );
```