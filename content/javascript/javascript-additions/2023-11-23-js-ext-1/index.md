+++
title = "Set"
draft = false
weight = 1
tags = ['javascript']
+++

Object Set memperbolehkan kamu menyimpan koleksi data yang *unique* dalam bentuk iterable.

## Constructor

```js
const newSet = new Set([1,1,2,2,3,4,4,5])
```
output: `Set {1, 2, 3, 4, 5}`

Dikarenakan isinya yang selalu unique, set tidak memiliki urutan. Tidak bisa diakses via indeks seperti halnya array.

### Mengubah Set tersebut menjadi array

```js
const setToArray = Array.from(newSet)
// same as
Array.from(new Set([1,1,2,2,3,4,4,5]))
```

## Menambah item

```js
newSet.add(8)
newSet.add(10)
```

output: `Set {1, 2, 3, 4, 5, 8, 10}`

## Mengecek item

`Set.prototype.has()` mengecek apakah nilai `x` ada didalam set. Hasil return dalam bentuk boolean

```js
const check = newSet.has(3)
console.log(check) //true
```

## Delete item

```js
newSet.delete(1)
```

output: `Set {2, 3, 4, 5, 8, 10}`