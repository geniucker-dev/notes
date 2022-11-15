## Input sources
1. From user: `input`  
2. From hard drive: `open(files)`  
    plain text file  
    comma-separated value file: `csv`
3. From internet: `requests`

### User input
`input(str)` which will return the string you input

### File input
#### 2 Ways to open a file
1. 
    ```python
    myFile = open('word.txt')
    ...
    myFile.close()
    ```
2. 
    ```python
    with open('word.txt') as myFile:
        ...
    ```

`2.` is better

#### 4 methods to read a files
1. `read()`  
2. `readlines()`  
3. `write()`  
4. `close()`  
5. or you can just read through a loop  

#### The csv format
csv: comma separated value  
##### Ways to read csv
- `readlines()` or `read()`  
- class `csv.DictReader`  
    approximate usage:  
```python
import csv
with open(fileName) as myFile:
    content = csv.DictReader(myFile,
                             # delimiter=',',  # ',' is default
                             # filednames=[0, 1, 2]  # None is default
                            )
    for i in content:  # each i is a dict
        print(i)
```
below is docs from Python:  
> `class csv.DictReader(f, fieldnames=None, restkey=None, restval=None, dialect='excel', *args, **kwds)`  
>   
> Create an object that operates like a regular reader but maps the information in each row to a `dict` whose keys are given by the optional fieldnames parameter.  
>   
> The fieldnames parameter is a sequence. ***If fieldnames is omitted, the values in the first row of file f will be used as the fieldnames.*** Regardless of how the fieldnames are determined, the dictionary preserves their original ordering.  
>   
> If a row has more fields than fieldnames, the remaining data is put in a list and stored with the fieldname specified by `restkey` (which defaults to `None`). If a non-blank row has fewer fields than fieldnames, the missing values are filled-in with the value of `restval` (which defaults to `None`)  
>   
> All other optional or keyword arguments are passed to the underlying reader instance.  
- `csv.reader()` (optional)  
    approximate usage:  
```python
import csv
with open(fileName) as myFile:
    content = csv.reader(myFile,
                         # delimiter=','  # ',' is default
                        )
    for i in content:
        print(i)  # i is a list
```

### Internet data/`requests`
```python
import requests
url = "https://cn.bing.com"
r = requests.get(url)
print(r.text)  # r.text is a string containing the html codes
```

