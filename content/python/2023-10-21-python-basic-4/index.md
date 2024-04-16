+++
title = "Python: List & Tuple"
draft = false
weight = 4
tags = ['python']
+++


## List

List serupa dengan array di JavaScript. Untuk membuat list kamu memerlukan list literal `,` dibungkus dengan `[]`.

```python
arr = ["Jeff", True, 28]
```

### List dua dimensi

List dua dimensi adalah list yang ada didalam list.

```python
arr = [["Jeff", True, 28], ["Amelia", False, 24]]
```

### Akses value

List memiliki index urutan item yang dimulai dari nol (*Zero Indexed*).

```python
arr = ["Jeff", True, 28]
print(arr[0]) # Prints "Jeff"

arr_2 = [["Jeff", True, 28], ["Amelia", False, 24]]
print(arr_2[0]) # Prints "["Jeff", True, 28]"
print(arr_2[1][2]) # Prints "24"
```

## List method

### Menambah value

`.append()` digunakan untuk menambahkan value ke list.

```python
arr_2 = [["Jeff", True, 28], ["Amelia", False, 24]]
arr_2.append(["Bob", True, 24])
print(arr_2)
```

### Hapus value

Menggunakan `.remove()` untuk menghapus value didalam list.

```python
arr = ["Jeff", True, 28]
arr.remove(True)
print(arr)
```

Menggunakan `.pop()` untuk menghapus value berdasarkan index.

```python
arr = ["Jeff", True, 28]
arr.remove(1)
print(arr)
```
Default argument `.pop()` adalah `-1`, yaitu menghilangkan item terakhir di list.

### Lainnya

Method list lainnya dapat ditemukan di [sini](https://www.w3schools.com/python/python_ref_list.asp) atau [disini](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)

## Tuple

List, Tuple, Dictionary dan Set adalah tipe data collection di python. Collection data type adalah jenis data type yang menyimpan lebih dari satu data.

Tuple tidak bisa diganti susunan awalnya, artinya data type ini "Read-Only". Tuple tetap memiliki index.

```python
thistuple = ("apple", "banana", "cherry", "apple", "cherry")
print(thistuple)
```

### Tuple satu item

Membuat tuple dengan satu item, kamu harus menambah koma `,` sesudah item tersebut.

```python
one_tuple = ("Alone",)
print(type(one_tuple)) # Akan print tipe data one_tuple
```

Pelajari tuple lebih lanjut [disini](https://www.w3schools.com/python/python_tuples.asp).