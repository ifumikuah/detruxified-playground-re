---
title: Pointer casting
date: 2024-05-26
weight: 3
tags:
  - C

resources:
  - name: img01
    src: "img/img01.png"
    title: ""
---

Casting tipe data C, casting tipe data akan mengubah tipe data sebuah variable. Narrow casting adalah casting tipe data dari yang terbesar ke terkecil.

Misal, konversi `short int` 16-bit ke `char` 8-bit akan memotong setengah dari memori yang di pakai oleh `short int` sebelumnya, jika ini dilakukan, maka value yang disimpan didalamnya menjadi corrupt.

Mari buat skenario:
```c
#include <stdio.h>

int main() {
  short int x = 1030;
  short int* ptr = &x;

  char* ptr0 = (char*) ptr;

  printf("%d\n", *ptr0);
  return 0;
}
```

`short int` dapat menampung integer -32,768 - 32,767. Casting ke `char` dilakukan terhadap variable `short int`.

{{< img name=img01 size=small >}}

Dikarenakan `char` hanya bisa menampung integer -128 - 127, maka akan membuat value yang didalamnya juga berubah, akibat "terpotong" saat dilakukan casting.
