+++
title = "Python: If Conditional Flows"
draft = false
weight = 3
tags = ['python']
+++

## If

`If`, Basic statement untuk mengendalikan logika kode. If harus mengevaluasi sebuah statement sebagai nilai boolean `True` agar block didalamnya dapat dieksekusi.

Statement harus menghasilkan nilai `True` atau bisa langsung memberikan nilai `True` secara eksplisit seperti dibawah ini.

```python
dont_skip = True

if (dont_skip):
    print("Thanks you didn't skip this part")

print("This always be printed")
```

## Elif

Cara kerja `elif` adalah "jika `If` tidak `True` maka coba statement ini".

```python
my_age = 24

if (my_age <= 12):
    print("You are below or at 12")
elif (my_age <= 24):
    print("You are below or at 24")

# Prints You are below or at 24
```

## Else

Blok `else` di eksekusi jika tidak ada statement yang terkualifikasi.

```python
my_age = 42.7

if (my_age <= 12):
    print("You are below or at 12")
elif (my_age <= 24):
    print("You are below or at 24")
else:
    print("You're too old")
```