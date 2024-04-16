+++
title = "Python: Intoduction and Basics"
draft = false
weight = 1
tags = ['python']
+++

Python, General multipurpose programming language yang populer setelah JavaScript. Bahasa ini digunakan untuk Software Engineering, AI dan automation.

## Data Types

Di Python, tidak perlu memberikan data type secara eksplicit, data types akan otomatis dikenali oleh interpreter.

Ada 4 data types primitif di python:

- `string`, sebuah karakter dibungkus dengan notasi string: `"String"`
- `integer`, sebuah bilangan dibulatkan: `24`
- `float`, sebuah bilangan dengan pemisah desimal: `3.14`
- `boolean`, disingkat bool, merupakan sebuah bit (0/1) yang merepresentasikan True / False: `True` dan `False`

Ada lagi data types seperti dictionary, list dan tuple, namun tidak akan dibahas disini.

## Commentary

Sebelum, membuat program `Hello World` yang terkenal, ada baiknya mengetahui cara komentar di python.

```python
# This is single line comment in python

"""
This is is also comment in python,
but its uses triple triple quotes.

As long it doesn't assigned to variable
python won't read this note.
"""
```

## Hello World

Mencetak sesuatu dengan `print()`.

```python
print("Hello World")
```

## Variables

Sebuah variable untuk menyimpan informasi.

```python
name_a_var = "This is string"
number = 25
```

## F string literals

Menggunakan f-string untuk format di print. Dimulai dengan memberikan notasi `f` sebelum memulai string.

```python
print(f"I am {number} years old").
# Outputs, I am 25 years old
```

{{< expand "Recap" "🧠" >}}
```python
# Defines variable
name = "John Malik"
age = 24

"""
Print it
It should output the string below
"""
print(f"{name}, you are at {age} now!")
```
{{< /expand >}}

## Mathematical operators

Membahas penggunaan operator basic `+`, `-`, `*`, `/`.

```python
num = 5

# Tambah
addtition = 10 + num
print(addition)

# Kurang
print(num - 2)

# Kali
print(5 * 3)

# Bagi
print(50 / num)
```