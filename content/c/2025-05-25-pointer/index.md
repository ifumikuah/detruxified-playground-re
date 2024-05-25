---
title: Pointer
date: 2024-05-25
weight: 30
tags:
  - C
---

Jika kita bisa mengakses alamat memori sebuah variable, maka kita juga bisa menyimpan alamat memori tersebut kedalam sebuah variable dengan pointer.

```c
int val = 56;
int* ptr = &val;
```

Pertama untuk membuat pointer, kita harus menggunakan `*` operator sesudah tipe data variable yang kita ingin buat pointernya, dalam contoh ini `val` merupakan sebuah `int`. Lalu buat nama variable contohnya `ptr` dengan value memory address dari `val` menggunakan reference operator `&`.

```c
#include <stdio.h>

int main() {
  int val = 56;
  int* ptr = &val;

  printf("val addres\t%p\n", ptr);
  printf("ptr address\t%p\n", &val);
  printf("sizeof ptr\t%d\n", sizeof(ptr));
  printf("sizeof val\t%d\n", sizeof(val));
  return 0;
}
```

## Dereference

Untuk mengakses value yang ada di pointer tersebut (dalam hal ini value dalam memory address), kita menggunakan dereference. Derefererece menggunakan operator yang sama dengan pointer `*`.

Tapi perlu diperhatikan, bahwa posisi `*` pada deklarasi pointer dan dereference sangatlah berbeda, deklarasi berada dipaling kanan sesudah deklarasi tipe data, sedangkan derefrence berada sebelum nama pointer.

```c
// Pointer declaration
int* ptr = &val;
```
```c
//  Dereference
int ptrval = *ptr;
```

```c
#include <stdio.h>

int main() {
  int val = 56;
  int* ptr = &val;

  printf("ptr value\t%d\n", *ptr);
  printf("val value\t%d\n", val);
  return 0;
}
```