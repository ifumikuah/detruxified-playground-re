---
title: File handling - read
date: 2024-06-09
weight: 32
tags:
  - C
---

## Membaca file

Gunakan `fopen()` dengan `r` read-mode untuk membaca sebuah file.

Untuk mengambil konten yang ada didalam file, kita menggunakan `fgets()`.

```c
fgets(flchar, 10, fptr);
```

Di agument pertama, `fgets` membutuhkan sebuah `char` variable untuk menyimpan tangkapan-nya, maka diatasnya itu kita harus mendeklarasi sebuah variable char.

```c
char flchar[10];
```

`fgets` hanya menangkap line pertama sebuah file jika didefinisikan tanpa perulangan seperti `while`.

```c
char flchar[10];
while (fgets(flchar, 10, fptr))
{
  printf("%s", flchar);
}
```

Kode diatas akan mencetak setiap line dari file yang dibuka/baca.

Fullcode:

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  FILE *fptr;
  fptr = fopen("players.txt", "r");

  char flchar[10];
  while (fgets(flchar, 10, fptr))
  {
    printf("%s", flchar);
  }
  fclose(fptr);

  return 0;
}
```