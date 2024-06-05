---
title: Pointer to pointer
date: 2024-05-26
weight: 8
tags:
  - C
---

Jika pointer menyimpan  alamat sebuah variable biasa, apakah pointer bisa menyimpan pointer? jawabannya bisa.

```c
int a = 21;
int* p = &a
int** r = &p
```

Diatas, r menyimpan alamat dari pointer `p`. dereference `r` hanya akan menunjukan angka acak yang tidak ada artinya, namun kita bisa dereference `p` melalui `r`.

```c
printf("%d", *(*r))
```

Diatas akan dua kali dereference, nilai `r`. Dereference nilai pertama membuka nilai `p` lalu dereference kedua membuka nilai `a`.