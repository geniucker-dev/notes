## `zip()`
[doc](https://docs.python.org/3/library/functions.html#zip)
```python
a = [1, 2, 3]
b = ['sugar', 'spice', 'everything nice']
print(list(zip(a, b)))
```
the result will be:
```shell
[(1, 'sugar'), (2, 'spice'), (3, 'everything nice')]
```
> By default, [`zip()`](https://docs.python.org/3/library/functions.html#zip "zip") stops when the shortest iterable is exhausted. It will ignore the remaining items in the longer iterables, cutting off the result to the length of the shortest iterable

## `enumerate()`
[doc](https://docs.python.org/3/library/functions.html#enumerate)
`enumerate(iterable, start=0)`
e.g.
```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']
print(list(enumerate(seasons)))
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
print(list(enumerate(seasons, start=1)))
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```