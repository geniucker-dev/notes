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