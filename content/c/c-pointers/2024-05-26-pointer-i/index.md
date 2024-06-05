---
title: Pointer address
date: 2024-05-26
weight: 1
tags:
  - C
---

Walaupun menyimpan alamat dari variable x, alamat variable pointer itu sendiri beda dengan alamat variable yang direferensikan.

```c
#include <stdio.h>

int main() {
  int x = 45;
  int* ptr = &x;

  printf("%p\n", ptr);
  printf("%p\n", &ptr); // Punya alamat sendiri 🤯
  printf("%d\n", *ptr);
  printf("%d\n", x);
  return 0;
}
```