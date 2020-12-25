# Fluent Python

## \#1: Python data model

### Special methods

* Allow custom objects to implement, support, and interact with basic language constructs \(e.g iteration, collections..\) 
* Also called magic methods or "dunder-foo\_name"
* Should not generally be called within python code \(are often called implicitly by executing representing  function\) 
* 🤔Note: for some build-in types python my take a shortcut and call a lower-level function \(pg 8\) - faster 



### Other notes

*  `collection.namedtuple`  - to create simple classes with no attributes and no custom methods \(example on pg 5\)
* `dunder-len` and `dunder-getitem` allows to operate with the class object behaves as Python sequence \(use len, indexing, slicing,  iterate over it etc\)

