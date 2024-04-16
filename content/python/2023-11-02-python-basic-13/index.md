+++
title = "Python: Dictionary"
draft = false
weight = 13
tags = ['python']
+++

Dictionary adalah tipe data mirip object di JavaScript.

Dictionary terdiri atas `key` dan `value`, sama halnya seperti object di JS

```python
var_dict = {
    "key": "value",
    "key_two": "value_two",
    "number": 3,
    4: "four"
}
```

## Basics

```python
animal = {
    "alpaca": "Johnny Smith"
}

## Menambah sebuah key
animal["horse"] = "Jaden Gonzalez"

## Mengubah value dari key yang sudah ada
animal["alpaca"] = "Ahmad Mansoor"
```

### Update

Method `update()` digunakan untuk menambahkan key baru lebih dari satu key.

```py
animal.update({
    "bear": "Simon McCharthy",
    "raven": "Simoleon Edward",
    "tuna": "Issac James"
})
```

### List Comprehension

Mengubah dua list menjadi sebuah dictionary menggunakan zip.

```py
drinks = ["espresso", "chai", "decaf", "drip"]
caffeine = [64, 40, 0, 120]

drinks_to_caffeine = {
    drink: caffeine for drink, caffeine in zip(drinks, caffeine)
}
# Try to print(drinks_to_caffeine)
```

## Method

Beberapa method basic dictionary adalah `items()`, `get()`, `keys()` dan `values()`.

### Mendapatkan key dan value

Menggunakan `items()` untuk menampilkan setiap `key` dan `value` dalam bentuk tuple.

```py
d = {1:'one', 2:'two', 3:'three'}
d_items = d.items()

# print(d_items) akan output sebuah tuple
```

Kita bisa iterate `d_items` dengan for loop.

```py
for num, string in d_items:
    print(f"{string} is string for number {num}")
```

### Get value dari key

Untuk mencari sebuah value dari key, gunakan `get()` dengan sintaks:

```plain
dictionary.get(key, default_value_if_nonexist)
```
```py
d = {1:'one', 2:'two', 3:'three'}
d.get(1, 'null') # return 'one'
d.get(8, 'null') # return 'null'
d.get(4) # return 'None'
```

### List Key

`keys()` akan return semua key dari dictionary sebagai list.

```py
d = {1:'one', 2:'two', 3:'three'}
d.keys() # print(d.keys()) Outputs [1, 2, 3]
```

### List Value

Sama seperti `keys()`, namun `values()` akan return value dari dictionary tersebut.

```py
d = {1:'one', 2:'two', 3:'three'}
d.values() # print(d.values()) Outputs ['one', 'two', 'three']
```

### Delete key

Gunakan `pop()` untuk menghapus key dari dictionary.

Cara kerja `pop()` sama seperti `get()`, nilai default adalah dictionary itu sendiri jika tidak diberikan argument kedua.

```py
d = {1:'one', 2:'two', 3:'three'}
d.pop(1, 'No Match') # Returns 'one'
d.pop(1) # Returns 'one'
d.pop(4, 'No Match') # Returns 'No Match'
d.pop(4) # An error raised
```
