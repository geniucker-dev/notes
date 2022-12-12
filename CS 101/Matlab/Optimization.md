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
xlabel( 'x' )：： 
ylabel( ’f(x)’ ) 
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