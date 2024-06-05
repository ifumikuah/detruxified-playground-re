---
title: Memory allocation
date: 2024-05-26
weight: 4
tags:
  - C

resources:
  - name: img01
    src: "img/img01.png"
    title: ""
  - name: img02
    src: "img/img02.png"
    title: ""
---
Alokasi memori di C. Didalam memory, setiap bytenya memiliki sebuah address. Jika sebuah variable dideklarasikan, maka value variable tersebut akan tersimpan di bytes yang dialokasikan, disebut juga dengan "memory block".

{{< img name=img01 size=small >}}

Alamat memori variable tersebut adalah alamat byte pertama dari block tersebut. Seperti contoh diatas, sebuah `int` (32-bit) memakan 4 byte memori, maka 4 byte dialokasikan untuk variable `x`.

Bagaimana, jika sebuah variable ditambahkan:

```c
#include <stdio.h>

int main() {
  int x = 1026;
  short int y = 513;
  int* ptrX = &x;
  short int* ptrY = &y;

  printf("%p\n", ptrX);
  printf("%p\n", ptrY);
  return 0;
}
```

Maka, otomatis blok memori variable tersebut diletakkan sesudah/sebelum variable sebelumnya. Posisi peletakkan blok ini dipengaruhi oleh pengaturan compiler masing-masing.

{{< img name=img02 size=small >}}

Dalam kasus ini, alamat blok `y` terletak sebelum alamat `x`.
