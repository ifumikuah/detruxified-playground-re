---
title: Void pointer
date: 2024-05-26
weight: 7
tags:
  - C
---

Di C ada void pointer.

```c
void* ptr;
```

```c
#include <stdio.h>

int main() {
  double x = 21.5783;
  short int y = 69;

  void* ptr = &x;

  printf("%p\n", ptr);
  return 0;
}
```

Void ini bisa menyimpan berbagai jenis tipe data, namun void tidak bisa di dereferensikan.