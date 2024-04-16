+++
title = "Python: Class (OOP Intro)"
draft = false
weight = 14
tags = ['python']
+++

Python adalah bahasa pemrograman OOP (Object Oriented Programming) language. Untuk membuat sebuah object custom kita sendiri, dibutuhkan sebuah constructor dan class.

## Class

Untuk membuat class, gunakan `class`.

```py
class NewClass:
    pass
```

Class diatas masih kosong tidak ada sesuatu didalamnya. Sekarang mari membuat sebuah variable:

```py
class NewClass:
    x = 42
```

Membuat sebuah objek dari class tersebut:

```py
var1 = NewClass()
print(var1.x) # Prints '42'
```

## Constructor

Class diatas adalah basic dari `class` yang tidak ada kegunaanya untuk sehari hari, umumnya jika kita membuat sebuah class, harus membuat sebuah constructor dan representasi dari class tersebut.

```py
class Projectile:
    def __init__(self, projectile_type, range):
        self.projectile_type = projectile_type
        self.range = range

missile_01 = Projectile("SAM Missile", 57)
print(missile_01.projectile_type) # Prints 'SAM Missile'
print(missile_01.range) # Prints '57'
```

- `self` merujuk kepada objek itu sendiri, yaitu `missile_01`.
- Disaat objek missile_01 di deklarasikan/dieksekusi, maka akan mentrigger fungi constructor yaitu `__init__`

### Self

Sebuah constructor/fungsi didalamnya wajib memiliki satu argument pertama untuk merujuk kepada objek itu sendiri. sebenarnya `self` dapat diganti dengan nama lain.

```py
class Projectile:
    def __init__(awyeah, projectile_type, range):
        awyeah.projectile_type = projectile_type
        awyeah.range = range

missile_01 = Projectile("SAM Missile", 57)
print(missile_01.projectile_type) # Prints 'SAM Missile'
print(missile_01.range) # Prints '57'
```

Yang menjadi keharusan adalah untuk membuat satu parameter pertama (`self`) di setiap fungsi  seperti yang dijelaskan diatas.

## Representation

Selain `__init__`, ada juga fungsi khusus untuk class yaitu `__repr__`, Merepresentasikan objek tersebut dengan string.

Defaultnya, jika mencoba untuk `print()` objek tersebut:

```py
print(missile_01)
# <__main__.Projectile object at 0x000002A5CCAC01A0>
```

Dengan memberikan, `__repr__` kita bisa membuat representasi string untuk objek tersebut
```py
class Projectile:
    # Constructor section

    def __repr__(self):
        return f"Type: {self.projectile_type}, Range: {self.range}"
```
```py
print(missile_01)
# Return 'Type: SAM Missile,Range: 57'
```