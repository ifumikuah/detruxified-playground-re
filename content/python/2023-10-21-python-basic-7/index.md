+++
title = "Python: Break dan Continue"
draft = false
weight = 7
tags = ['python']
+++

Mengatur perulangan dengan `break` dan `continue`.

## Break

Kita ingin membuat sebuah filter yang membatasi umur seseorang untuk masuk.

```python
ages = [31, 24, 28, 21, 20, 25, 39, 20]
for age in ages:
    if age < 21:
        break
    print(f"Age {age}, Pass")
```

## Continue

Sangat tidak masuk akal jika seseorang tidak terkualifikasi, perulangan langsung batal.

```python
ages = [31, 24, 28, 21, 20, 25, 39, 20]
ages_i = 0
for age in ages:
    if age < 21:
        continue
    print(f"Age {age}, Pass")
    ages_i += 1

print(f"{ages_i} out of {len(ages)} candidates pass the test")
```

Continue digunakan untuk melompati sebuah item yang tidak sesuai kriteria.