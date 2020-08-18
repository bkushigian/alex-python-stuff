# Week 1 Problems

## 1. Add Numbers
Write a script that adds all the numbers given to it from command line.

### Using `argv`
You'll want to use the `argv` variable from the `sys` module. This gives you
access to the command line arguments (`argv` stands for "Argument Vector", and
'vector' just means a list)

```python
from sys import argv
print(argv)
```

If the above is called `my-script.py`, then running `python my-script.py hi lo
left right` will yield:

```shell
$ python my-script.py hi lo left right
['my-script.py', 'hi', 'lo', 'left', 'right']
```

### Lists
`argv` returns a `list` (which is a Python data structure) where the first
element is the name of the script that was called, and the remaining elements
are the arguments passed in from command line.

#### Indexing
Lists are _zero-indexed_:

```python
my_list = ["first item", "second item", "third item"]
print(my_list[0])  # Prints "first item"
print(my_list[1])  # Prints "second item"
print(my_list[2])  # Prints "third item"
```

This is confusing to many new coders, but you'll get used to it real fast :)

Note the `list_name[n]` syntax. This is called _indexing_, and gives you back
the `n`th item in the list. Be careful, though, this can easily blow up!

```python
print(my_list[3])  # Blows up :(
```

#### Slicing
While indexing lets you work with single values at a time, _slicing_ lets you
work with a bunch of values at once. Check this out:
```python
my_list = list(range(10))  # Literally [0,1,2,3,4,5,6,7,8,9]
print(my_list)       # Prints [0,1,2,3,4,5,6,7,8,9]
print(my_list[5])    # Prints 5
print(my_list[1:3])  # [1,2]
```
The last line uses the `list_name[low:hi]` syntax. This takes a list and returns
a sub-list with the elements at indices from `low` (inclusive), to `hi`
(exclusive). Note the asymmetry: the `low` index is included in the list, but
the `hi` index is not. This is very nice but might take some getting used to.

### Using Slicing to Get The Args
Okay, so you want to drop the first arg from `argv`. How do you do this? Well,
you can use a slice:

```python
my_args = argv[1:]
```

Note the new syntax: I'm not specifying the `hi` index in the above slice. Using
this syntax starts at `lo` (in this case, `1`), and goes to the end of the list.
This is equivalent to `argv[1:argv.len()]`.

### Looping
You can look at each element in a list in turn by using the `for` loop:
```python
# Prints numbers 1, 2, 3 on their own lines
for x in [1,2,3]:
    print(x)
```

So if you wanted to print the args that were supplied from command line you
could write this like:

```python
from sys import argv

for arg in argv[1:]:    # Drop the name of the script
    print(arg)
```

