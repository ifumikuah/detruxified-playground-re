---
title: Pointer reassign value
date: 2024-05-26
weight: 2
tags:
  - C
---

Reassign value dari pointer.

```c
int x = 10;
int* ptr = &x;

int y = 30;
*ptr = y; 
```

`*ptr` dereference pointer, lalu reassign value awalnya menjadi value `y`. Hal ini merupakan cara yang sama dengan assign value `x = y`.

```c
*ptr = y; 
// Sama dengan
x = y;
```

Lalu lihat hasil `x` yang sekarang. Value diubah melalui akses alamat memorinya.

```c
printf("%d\n", x);
```