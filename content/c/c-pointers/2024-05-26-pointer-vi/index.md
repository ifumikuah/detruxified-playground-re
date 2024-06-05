---
title: Pointer arithmetic II
date: 2024-05-26
weight: 6
tags:
  - C

resources:
  - name: img01
    src: "img/img01.png"
    title: ""
---

Kita sudah mempelajari konsep sederhana dari pointer aritmethic, lalu apa gunanya, dan apa tujuannya. Well, semenjak pointer aritmethic dapat travese antar alamat memori, ini bisa menjadi curse and blessings.

```c
#include <stdio.h>

int main() {
  short int x = 1024;
  short int y = 513;
  short int z = 128;
  short int* ptrZ = &z;

  *(ptrZ+2) *= 2;
  *(ptrX-2) *= 2;

  printf("%d\n", x);
  printf("%d\n", z);
  return 0;
}
```

`*(ptrZ+2) *= 2;` akan dereference `ptrZ+2`, yaitu value `x` dan mengkalikan 2 + reassign value dari alamat memori tersebut. Hal seperti ini mempermudah kita memanipulasi array.

Tapi sisi buruknya, aritmethic yang terlalu kompleks dapat mengakses alamat memori yang tidak diinginkan dan beresiko membuat program tersebut corrupt.

## Cool trick

```c
#include <stdio.h>

int main() {
  int val = 16910595;
  int* ptrVal = &val;
  char* ptrChar = (char*) ptrVal;

  for (int i = 0; i < sizeof(val) / sizeof(char); i++)
  {
    printf("ptr val: %d\n", *(ptrChar+i));
  }
  return 0;
}
```

Kode diatas akan mencetak, integer setiap byte dari `val`. Pertama kita membuat sebuah pointer yang menggunakan data type sebesar 1 byte. Satu-satunya data type yang memakan 1 byte adalah `char`, kita akan menggunakan pointer char `ptrChar` untuk meng-iterate setiap byte dari `val`.

{{< img name=img01 size=small >}}

Untuk membuat address `ptrChar` sama dengan `ptrVal`, kita akan casting `ptrVal` ke tipe data `char`, tentunya ini akan memotong bytes dari `val`, menyisakan byte pertamanya.

`sizeof(val) / sizeof(char);` Membagi besar tipe data yang dipakai `val` dengan besar tipe data `char`, digunakan untuk agar tahu berapa kali iterasi yang harus diulang.


Dengan begitu, pengulangan ini akan mencetak value dari alamat memori setiap byte nya menggunakan pointer arithmetic `ptrChar` .
