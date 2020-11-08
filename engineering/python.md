# Python

{% embed url="https://docs.python-guide.org/" %}

## Q&A: 

### `__all__`

{% embed url="https://stackoverflow.com/questions/44834/can-someone-explain-all-in-python" %}

**NOTE:** `__all__` affects the `from <module> import *` behavior only. Members that are not mentioned in `__all__` are still accessible from outside the module and can be imported with `from <module> import <member>`.



