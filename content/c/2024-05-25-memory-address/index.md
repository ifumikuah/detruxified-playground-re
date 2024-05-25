---
title: Memory address
date: 2024-05-25
weight: 29
tags:
  - C
---

Setiap variable yang dideklarasi di C, tersimpan di dalam memory dan terdapat alamat memorinya.

```c
#include <stdio.h>

int main() {
  int val = 56;
  int val2 = 56;

  printf("%p\n", &val);
  printf("%p\n", &val2);
  return 0;
}
```

Alamat berbentuk dalam hexadecimal (base-16), untuk mengakses alamatnya, gunakan reference operator`&`. Untuk mencetak, gunakan pointer format specifier `%p`.