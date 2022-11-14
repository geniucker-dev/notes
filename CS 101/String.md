## Methods
[doc](https://docs.python.org/3/library/stdtypes.html#string-methods)
- `str.split(sep=None, maxsplit=-1)`:  
    `sep`: the delimiter string  
    `maxsplit`: if given, at most `maxtsplit` splits are done, so the list will contain `maxtsplit+1` elements  
> If `sep` is not specified or is None, a different splitting algorithm is applied: runs of consecutive whitespace are regarded as a single separator, and the result will contain no empty strings at the start or end if the string has leading or trailing whitespace. Consequently, splitting an empty string or a string consisting of just whitespace with a None separator returns [].
- `star.join(aListOrStr)`  
- `str.lower()`  
- `str.upper()`  
- `str.count(aStr)`  
- `str.replace(s1, s2)`: return a str where `s1` is replaced by `s2`  
- `str.strip()`: remove whitespace at both ends  
- `str.title()`: capitalize the first letter of each word  

- `str.isdigit()`  
- `str.isalpha()`  
- `str.isalnum()`  
- `str.islower()`  
- `str.isupper()`  