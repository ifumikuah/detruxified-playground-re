+++
title = "Python: Strings"
draft = false
weight = 10
tags = ['python']
+++

## String Iteration

String adalah tipe data *iterable* immutable, itu artinya string memiliki cara kerja yang mirip dengan tuple atau list.

- String tidak dapat diubah langsung dalamnya (Immutable)
- Setiap karakter memiliki indeks di posisinya.
- Dapat memotong/slice sebagian dari string.
- Dapat di *concatenete*
- Mengeja/iterate setiap karakter menggunakan for loop

### Slicing String

```python
str_one = "watermelon" # Sets a string
print(str_one[3:6]) # Prints "erm"
print(str_one[5:]) # Prints "melon"
print(str_one[:5]) # Prints "water"
print(str_one[5:] + str_one[:5]) # Prints "melonwater"
```

Kamu juga bisa memotong indeks dari belakang menggunakan angka minus.

```python
str_one = "watermelon" # Sets a string
print(str_one[-1]) # Prints huruf terakhir dari strings
print(str_one[-4:]) # Prints "elon"
```

### For loops

```python
str_one = "watermelon"
for char in str_one:
    print(char)     # Print char sequentially
```

Dengan for loop, kamu bisa manipulasi string tersebut dengan method yang dijelaskan dibawah.

## Method

Semua method dapat ditemukan [disini](https://www.w3schools.com/python/python_ref_string.asp).

### Membuat sandi caesar

Membuat sandi caesar dengan 3 geseran ke kanan.

```python
def caesar_encode(input):
    alphabets = "abcdefghijklmnopqrstuvwxyz"
    output = [] # Preping an empty list for output
    for char in input:
        # Preparing letter from alphabets to shift to by taking correspondent letter indices
        shift_target = alphabets.find(char) + 3 # this will shift 3 char to the left
        shift_target %= len(alphabets) # you need to prevent shift_target from exceeding alphabets char limit (26)
        output.append(alphabets[shift_target])
    return "".join(output) # Cunvert the list into string
```

Fungsi diatas hanya berfungsi untuk string satu kata (tanpa spasi).