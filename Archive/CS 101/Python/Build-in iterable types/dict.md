## Notice!!!
> `a = {'a': 1, 'b':1, 'a': 2}`
> the result of a will be `{'a': 2, 'b': 1}`
## methods
- `dict[key]`
- `dict.get(key[,default])`: similar to `dict[key]`. Return the value for key if key is in the dictionary, else default. If default is not given, it defaults to `None`, so that this method never raises a `KeyError`. Of course, you can't use this to change the value of a `dict`  
- `dict.items()`: `list({'one': 1, 'two': 2}.items())` is `[('one', 1), ('two', 2)]`
- `dict.keys()`
- `dict.values()`

## sort a dict
there's no `dict.sort`, so we need to  
1. change `dict` into a `list`  
2. use `list.sort(key=fn)` or `sorted(yourList, key=fn)`
3. convert result back to `dict`
e.g.  
```python
myD = {'five': 5, 'three': 3, 'four': 4}

myL = list(myD.items())
myL.sort(key=lambda x:x[1])

myD2 = dict(myL)
```