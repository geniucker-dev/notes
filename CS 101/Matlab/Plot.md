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
- `fplot`: plot an equation
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
