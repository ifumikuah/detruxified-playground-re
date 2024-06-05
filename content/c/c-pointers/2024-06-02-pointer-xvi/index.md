---
title: Pointer return function
date: 2024-06-02
weight: 16
tags:
  - C
---
Kali ini akan membuat sebuah fungsi yang mereturn sebuah pointer. Jika sebuah array decease menjadi sebuah pointer, apakah kita bisa membuat array sendiri secara dinamis.

Jawabannya bisa menggunakan fungsi yang akan return sebuah pointer. Tapi sebelum itu mari pahami mekanisme sederhana dari fungsi yang akan return sebuah pointer.

Prototype:

```c
int *mkarray(int n);
```

Deklarasi fungsi diatas akan return sebuah pointer, yaitu alamat memori.

```c
#include <stdio.h>
#include <stdlib.h>

int *mkarray(int n);

int main() {
  int* x = mkarray(45);

  printf("value is: %d\n", *x);
  printf("Hello\n");
  return 0;
}

int *mkarray(int n) {
  int* ptr = &n;
  return ptr;
}
```

Tetapi apa yang terjadi jika urutan call function kita ubah.

```c
printf("Hello\n");
printf("value is: %d\n", *x);
```

Output tidak sesuai dengan ekspetasi kita. Ini dikarenakan value yang direturn oleh fungsi `mkarray()` tersimpan didalam stack.

Di stack, fungsi yang sudah selesai/return sebuah nilai akan dibersihkan dan alamatnya dipakai untuk fungsi yang selanjutnya.

dalam hal ini, ketika `mkarray()` sudah dipanggil sekali dan valuenya disimpan oleh `x`, alamat yang dipakai oleh `mkarray()` sebelumnya dipakai lagi oleh fungsi `printf("Hello\n")`, Ini membuat value yang berada didalam `x` sebelumnya sudah hilang duluan sebelum  value dari `x` digunakan lagi untuk output statement print sesudahnya.

Untuk mengatasi hal ini, kita perlu suatu kondisi dimana kita bisa secara eksplisit mengatur kapan dan sebesar apa memori dibuat dan kapan saja kita yang membebaskannya.

Kita akan menggunakan heap untuk menyimpan return value dari `mkarray()`.

```c
int *mkarray(int n) {
  int* ptr = (int*) malloc(sizeof(int));
  *ptr = n;
  return ptr;
}
```

Ini akan mengalokasikan 4 bytes dan value disimpan oleh pointer `ptr` yang ada di heap. Dan setelahnya kita bebas untuk membebaskan memori yang dipakai tersebut kapan saja.

```c
#include <stdio.h>
#include <stdlib.h>

int *mkarray(int n);

int main() {
  int* x = mkarray(45);

  printf("Hello\n");
  printf("value is: %d\n", *x);
  free(x);
  return 0;
}

int *mkarray(int n) {
  int* ptr = (int*) malloc(sizeof(int));
  *ptr = n;
  return ptr;
}
```
