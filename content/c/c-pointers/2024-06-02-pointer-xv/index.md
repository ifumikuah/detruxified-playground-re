---
title: Realloc
date: 2024-06-02
weight: 15
tags:
  - C
---
`realloc()` re-alokasi memori yang digunakan sebelumnya, menambah atau menguranginya.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
  int* x = (int*) calloc(3, sizeof(int)); // 3*4 = 12 bytes of memory
  x[0] = 15;
  x[1] = 20;
  x[2] = 25;

  for (size_t i = 0; i < 3; i++)
  {
    printf("%d \n", x[i]);
  }

  printf("\n");

  x = (int*) realloc(x, 5 * sizeof(int)); // 5*4 = 20 bytes of memory
  x[3] = 30;
  x[4] = 35;

  for (size_t i = 0; i < 5; i++)
  {
    printf("%d \n", x[i]);
  }

  return 0;
}
```

Kode diatas merelokasi memori yang sebelumnya 12 bytes digunakan, lalu mengubah menjadi 20 bytes untuk digunakan.

```c
x = (int*) realloc(x, 5 * sizeof(int));
x[3] = 30;
x[4] = 35;
```

## Realloc as malloc

Realloc bisa menjadi alternatif dari fungsi `malloc()`.

```c
int* x = (int*) realloc(NULL, 4 * sizeof(int));
```

Ketika argument pointer diisi oleh `NULL`, maka akan membuat alokasi baru di heap, kode diatas sama dengan syntax `realloc(4 * sizeof(int))`.

## Realloc as free

Realloc bisa juga menjadi alternatif dari `free()` jika pointer diisi dengan pointer dari alokasi yang sudah ada dan argumen size diisi nol `0`.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
  int* x = (int*) realloc(NULL, 3 * sizeof(int));
  x[0] = 15;
  x[1] = 20;
  x[2] = 25;

  for (size_t i = 0; i < 3; i++)
  {
    printf("%d \n", x[i]);
  }
  
  realloc(x, 0);
  return 0;
}
```

Namun, cara ini tidak disarankan. Selalu gunakan `free()` untuk membebaskan memori alokasi.