# Bash

### Find a pattern in a file 

```text
grep -rnw '/path/to/somewhere/' -e 'pattern'
```

* `-r` or `-R` is recursive,
* `-n` is line number, and
* `-w` stands for match the whole word.
* `-l` \(lower-case L\) can be added to just give the file name of matching files.

### Find a file by name

```text
find /dbfs/ -name "weather_bobo"
```

### Conda

Create env with python 3.6.

```text
conda create -n mlflowdbx python=3.6
```

### Virtualenv

```text
python3 -m venv env
source env/bin/activate
```



