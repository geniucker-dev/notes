e.g.
```MATLAB
x = 0:.1:2*pi;
y = sin(x);

figure(100);  % greates a new figure (window for plots)
plot(x, y,, 'o');  % works identically to plt.plot in py
title('sinx(x)');
xlabel('x  values');
ylabel('y values');
```

other functions used for plotting
- `fplot`: plot an equation, ***can plot both equation and parametric equation***
- `plot3`: 3D plot
- `fcontour`: plot contour
- `subplot`: small plots within a plot

If you want to plot a second plot without removing the previous one, use `hold on;`
```MATLAB
figure(1);
% plot the first one here
hold on;
% plot the second one here
```

`subplot`:
```MATLAB
figure(2)  %create a new figure numbered 2
f = @(x, y) sin(x) + cos(y);
fcontour(f);  % plot a contour plot
x = linspace(0,10);
subplot(2,1,1);  % divide graph into 2 rows 1 column and use subplot 1
y1 = sin(x);
plot(x,y1);
subplot(2,1,2);  % use subplot 2
y2 = sin(5*x);
plot(x,y2);
```
the result is like this:
![[Archive/CS 101/Matlab/Plot/image/1.png|400]]
