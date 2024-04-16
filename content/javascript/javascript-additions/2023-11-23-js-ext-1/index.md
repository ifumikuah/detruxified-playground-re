+++
title = "Javascript Additions: Set"
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

### Mengubah Set tersebut menjadi array

```js
const setToArray = Array.from(newSet)
// same as
Array.from(new Set([1,1,2,2,3,4,4,5]))
```