---
title: Generate random integer
date: 2024-05-23
weight: 27
tags:
  - C
---

Gunakan `rand()` untuk generate angka random. `rand()` didapat dari library `stdlib.h`. Normalnya, `rand()` generate angka random dari 0 sampai `RAND_MAX`.

Untuk `RAND_MAX` nilainya tergantung, berdasarkan mayoritas sumber: 

> *RAND_MAX is a constant whose default value may vary between implementations but it is granted to be at least 32767*

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  for (int i = 0; i < 10; i++)
  {
    printf("%d\n", (rand() % 6) + 1);
  }
  
  return 0;
}
```

Diatas akan generate random integer dari 1 sampai 6.

Namun, keanehan terjadi jika kamu mengeksekusi kode berulang kali, angka random yang ditampilkan tidak pernah berubah dari yang sebelumnya, ini tidak benar-benar random.

Untuk mengatasinya, kita perlu mengubah *seed* yang dipakai oleh `rand()`. Seed ini berasal dari library `time.h`, yaitu `srand()`, *seed random*.

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
  srand(time(0));

  for (int i = 0; i < 10; i++)
  {
    printf("%d\n", (rand() % 6) + 1);
  }
  
  return 0;
}
```