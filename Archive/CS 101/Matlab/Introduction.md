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
    A = 0:10:100  % same as the A above
    B = A(4:7)  % ends included
    ```
- Multidimensional arrays
   e.g.
   ```MATLAB
   A = [1 2 3; 4 5 6]  % 2x3 matrix
    ``` 
- `ones()`, `eye()`, `zeros()` are similar to those in python  
    `ones(n)` is identical to `ones(n, n)`

### Scalar / Array Operations
#### Array operators
1. Basic (Scalar) mathematics
    - `A = [1 1] + 1`  
    - `B = sin(ones(3, 3) * pi)`  
    - `C = B'`: the transpose of B
    - `A = ([1 1] + 1) ./ 2`: same as above
    - `B = sin(ones(3, 3) .* pi)`: same as above
2. **Matrix** calculation
    - `D = eye(3, 4) * ones(4, 5) * pi`
    > `.*` and `./` is for scalar mathematics or element-wise calculation  
    > `*` is for matrix operation. MATLAB will try matrix operation first. If cannot, then scalar calculation. If still cannot, give an error. 
    
    - `E = inv(A)`: the matrix inverse
        `inv(P) * Q` is identical to `Q \ P`
    
### String / Char Array
> Single quotes creates `char array`
> Double quotes creates `string`

```MATLAB
s = 'I know this';
bigS = "Different? What? Confused!";
s(1)  % 'I'
bigS(1)  % "Different? What? Confused!"
bigS{1}  % 'Different? What? Confused!''
bigS{1}(1:2)  % 'Di'

```
> But be careful—sizes cause surprises.

```MATLAB
A = ['HELLO';'WORLD' ];
C = ['HELLO';'WORLD!' ];  % Fail!!!
```
***the second line will fail, because the length of two elements are not the same***
but
```MATLAB
A = ["HELLO";"WORLD" ];
C = ["HELLO";"WORLD!" ];
```
both are OK.

## Loop
#### for loop
```MATLAB
for variable = range, 
    % where you create var and provide range 
    one or more statements
end
```
Can use continue and break as in python
e.g.
```MATLAB
for i = 1:2:10  %Start:Step:End
    fprintf( ’The number is %i.’ , i );
end
```
also
`for i = charArray`
there is also `linspace()`
#### while loop
e.g.
```MATLAB
i = 0;
while i < 10
    i = i + 1;
    fprintf( ’The number is %i.’ , i );
end
```

## If and logic
### if/else statement
```MATLAB
if expr
    ...
elseif expr
    ...
else
    ...
end
```
### Logical statements
> MATLAB does ***NOT*** have a `bool` data type. USE `0` or `1`
> MATLAB will recognizes `false` and `true` as `0` and `1`, **but in data type `logical`

- `<`, `>`, `<=`, `>=`, `==`, `~=`
- `&`, `&&` means 'and'
- `|`, `||` mean 'or'

```MATLAB
A = [1, 5, 1; 3, 6, 2];
A(A>2)
% equals to [3 5 6]'
```

## Random numbers
- `rng(n)`: set the seed
- `rand(sz1, sz2,...)`: generate a matrix of size sz1 x sz2 x ... with uniform distribution between (0, 1). If there's only one parameter, same as `rand(sz1, sz1)`
- `randn(sz1, sz2, ...)`: normal distribution with mean 0 and variance 1
- `randi()`: random integers between [1, n]