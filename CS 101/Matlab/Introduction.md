[doc](https://ww2.mathworks.cn/help/matlab/)
- if you need help about something, you can use `help something` or `doc something`
    e.g. `help sort`

### Array in MATLAB
```MATLAB
a = [1 2 3];  %row vector
b = [1 2 3]';  % or b = [1; 2; 3]  % column vector
A = [1 2 3; 4 5 6];  % matrix
```
> ***MATLAB start from `1` NOT `0`***

- index array:
    ```MATLAB
    a = [1 2 3 4 5 6 7 8 9];
    b = a(1);  % 1
    A = [0 10 20 30 40 50 60 70 80 90 100];
    B = A([5, 9, 2, 2]);  % [1 6 2 2]
    ```
    we can also use slice
    ```MATLAB
    A = 
```