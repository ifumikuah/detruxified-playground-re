+++
title = "Python: Functions"
draft = false
weight = 9
tags = ['python']
+++

Membuat fungsi di python.

```python
def my_function():
  print("Hello from a function")
```
Mengeksekusi fungsi tersebut dengan memanggilnya

```python
my_function()
```

## Return

Fungsi didalamnya akan *return* sebuah value.

```python
def power_of(base, exponent):
    return base**exponent
```
```python
print(power_of(2, 64)) # Prints max bits of a data can be stored in 64 bit architecture computer
```