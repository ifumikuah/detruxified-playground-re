+++
title = "Python: Loops"
draft = false
weight = 6
tags = ['python']
+++

Melakukan perulangan di python.

## For loop

`for` loop melakukan perulangan berdasarkan e.g: list, tuple, string, dictionary atau set.

```python
objects = ["car", "train", "watermelon", "mug", "spoon"]
initial_len = 0
for x in objects:
    print(f"{x} at index {initial_len}")
    initial_len += 1
```

### String loop

Kita dapat mengakses sebuah karakter yang ada di sebuah string sama halnya seperti list.

```python
# Prints each character in variable astring
astring = "mississipi"

for char in astring:
    print(char)
```
```python
# Convert astring to a list
astring = "mississipi"
alist = []

for char in astring:
    alist.append(char)

print(alist)
```
An easier way to do that is just:
```python
alist = list(astring)
```

## Range function

Fungsi `range()` bisa juga digunakan untuk for loop.

```python
# Print Hi 8x
for x in range(8):
    print("Hi")
```

## While loop

Bentuk loop yang akan terus berjalan selama memiliki nilai `True`.

```python
# Print Hallo sampai i < 10
i = 0
while i < 10:
    print("Hallo", i)
    i += 1
```