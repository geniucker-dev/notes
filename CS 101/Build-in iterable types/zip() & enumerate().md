## `zip()`
[doc](https://docs.python.org/3/library/functions.html#zip)
```python
a = [1, 2, 3]
b = ['sugar', 'spice', 'everything nice']
print(list(zip(a, b)))
```
the result will be:
```
[(1, 'sugar'), (2, 'spice'), (3, 'everything nice')]
```
> By default, [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") stops when the shortest iterable is exhausted. It will ignore the remaining items in the longer iterables, cutting off the result to the length of the shortest iterable

## `enumerate()`
[doc](https://docs.python.org/3/library/functions.html#enumerate)