# Python



{% embed url="https://learnxinyminutes.com/docs/python/" caption="code snippets are from here" %}

{% embed url="https://docs.python-guide.org/" %}

## Q&A: 

### `__all__`

{% embed url="https://stackoverflow.com/questions/44834/can-someone-explain-all-in-python" %}

**NOTE:** `__all__` affects the `from <module> import *` behavior only. Members that are not mentioned in `__all__` are still accessible from outside the module and can be imported with `from <module> import <member>`.

### `__init__`

{% embed url="https://docs.python-guide.org/writing/structure/\#packages" %}

Any directory with an `__init__.py` file is considered a Python package. The different modules in the package are imported in a similar manner as plain modules, but with a special behavior for the `__init__.py` file, which is used to gather all package-wide definitions.

A file `modu.py` in the directory `pack/` is imported with the statement `import pack.modu`. This statement will look for an `__init__.py` file in `pack` and execute all of its top-level statements. Then it will look for a file named `pack/modu.py` and execute all of its top-level statements. After these operations, any variable, function, or class defined in `modu.py` is available in the pack.modu namespace.

## is vs '=='

is checks if two variables refer to the same object, but == checks if the objects pointed to have the same values.

## Strings

```text
# A string can be treated like a list of characters
"Hello world!"[0]  # => 'H' 
```

```text
# You can basically put any Python expression inside the braces and it will be output in the string.
f"{name} is {len(name)} characters long." # => "Reiko is 5 characters long."
```

## None

```text
# None is an object
None  # => None

# Don't use the equality "==" symbol to compare objects to None
# Use "is" instead.
```

## Boolean\(x\)

```text
# None, 0, and empty strings/lists/dicts/tuples all evaluate to False.
# All other values are True
bool(0)   # => False
bool("")  # => False
bool([])  # => False
bool({})  # => False
bool(())  # => False
```

## Variables

```text
# There are no declarations, only assignments.
```

## List 

### Indexing

```text
# You can look at ranges with slice syntax.
# The start index is included, the end index is not
# (It's a closed/open range for you mathy types.)
li[1:3]   # Return list from index 1 to 3 => [2, 4]
li[2:]    # Return list starting from index 2 => [4, 3]
li[:3]    # Return list from beginning until index 3  => [1, 2, 4]
li[::2]   # Return list selecting every second entry => [1, 4]
li[::-1]  # Return list in reverse order => [3, 4, 2, 1]
# Use any combination of these to make advanced slices
# li[start:end:step]
```

### Make deep copy

```text
# Make a one layer deep copy using slices
li2 = li[:]  # => li2 = [1, 2, 4, 3] but (li2 is li) will result in false.
```

### Remove value

```text
# Remove first occurrence of a value
li.remove(2)  # li is now [1, 3]
li.remove(2)  # Raises a ValueError as 2 is not in the list
```

### Remove element 

```text
# Remove arbitrary elements from a list with "del"
del li[2]  # li is now [1, 2, 3]
```

### Insert at index

```text
# Insert an element at a specific index
li.insert(1, 2)  # li is now [1, 2, 3] again
```

### Get index of first occurence

```text
# Get the index of the first item found matching the argument
li.index(2)  # => 1
li.index(4)  # Raises a ValueError as 4 is not in the list
```

## Tuples

```text
# Tuples are like lists but are immutable.
tup = (1, 2, 3)
tup[0]      # => 1
tup[0] = 3  # Raises a TypeError
```

## Update default python version 

{% embed url="https://dev.to/malwarebo/how-to-set-python3-as-a-default-python-version-on-mac-4jjf" %}



