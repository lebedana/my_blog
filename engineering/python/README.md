# Python

{% embed url="https://docs.python-guide.org/" %}

## Q&A: 

### `__all__`

{% embed url="https://stackoverflow.com/questions/44834/can-someone-explain-all-in-python" %}

**NOTE:** `__all__` affects the `from <module> import *` behavior only. Members that are not mentioned in `__all__` are still accessible from outside the module and can be imported with `from <module> import <member>`.

### `__init__`

{% embed url="https://docs.python-guide.org/writing/structure/\#packages" %}

Any directory with an `__init__.py` file is considered a Python package. The different modules in the package are imported in a similar manner as plain modules, but with a special behavior for the `__init__.py` file, which is used to gather all package-wide definitions.

A file `modu.py` in the directory `pack/` is imported with the statement `import pack.modu`. This statement will look for an `__init__.py` file in `pack` and execute all of its top-level statements. Then it will look for a file named `pack/modu.py` and execute all of its top-level statements. After these operations, any variable, function, or class defined in `modu.py` is available in the pack.modu namespace.

### Update default python version 

{% embed url="https://dev.to/malwarebo/how-to-set-python3-as-a-default-python-version-on-mac-4jjf" %}



