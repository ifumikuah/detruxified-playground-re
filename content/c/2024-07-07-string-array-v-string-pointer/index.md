---
title: String array vs. string pointer
date: 2024-07-07
weight: 38
tags:
  - C
---

Ada 2 cara untuk membuat sebuah string:

1. Menggunakan array:
```c
char str[] = "Bread";
```

2. Menggunakan pointer:
```c
char* str = "Bread";
```

Keduanya sama-sama mencetak sebuah string. Namun, terdapat perbedaan antara menggunakan array dan pointer.

## String Array

```c
char str[] = "Bread";
```

String array menyimpan sebuah string dengan mencopy satu-per-satu *char* ke memori yang sudah dialihkan. Seperti contoh diatas, program akan melakukan:

1. Membuat sebuah array yang terdiri atas `strlen("Bread")` buah char (alokasi).
2. Menyalin satu-per-satu karakter yang ada di **Bread** ke posisi yang sesuai (copying).

Ketika array dibuatkan artinya array `str` tersebut bersifat *read-write*, isi didalamnya bisa dimodifikasi.

## String Pointer

```c
char* str = "Bread";
```

String pointer menyimpan string langsung ke dalam sebuah *read-only* memory yang sudah dialokasikan sebesar `str` tersebut.

Kompiler mengalokasikan pointer tersebut ke sebuah blok memory *read-only*, artinya value didalamnya tidak bisa kita modifikasi.

## Test

```c
#include <stdio.h>

int main() {
  char sar[] = "butter";
  char* sptr = "bread";

  sptr[0] = 'c';
  printf("%s \n", sptr);
  return 0;
}
```

Kode diatas menghasilkan segfault karena kamu mencoba mengakses memori yang tidak diizinkan untuk diakses.