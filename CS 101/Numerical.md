## floats in binary
$$\begin{align}
5.375 &= 2^2 + 2^0 + 2^{-2} + 2^{-3}\\
     &= 101.011\\
     &= .101011*2^{11}\end{align}$$
`.101011` is called **mantisa**  
the superscript `11` is called **exponent**  
64 bits float => 53 bits mantissa + 10 bits exponent + 1 bit sign  
## How to compare floats?
- `math.isclose(a, b, rel_tol=1e-05, abs_tol=1e-08)`: compares numbers
- `np.isclose( a, b, rtol=1e-05, atol=1e-08)`: compares numbers or individual numbers in **an array** or list or tuple. It returns an array of bool if it compares an array or list or tuple.
- `np.allclose(a, b, rtol=1e-05, atol=1e-08)`: returns only **a single bool**.
