---
title: Pointer arithmetic
date: 2024-05-26
weight: 5
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

Pointer arithmetic adalah teknik untuk melompat/travese antar blok memori.

{{< img name=img01 size=small >}}

Berdasarkan diagram diatas, akan kemana kah `ptrZ+1` menuju?

```c
#include <stdio.h>

int main() {
  short int x = 1026;
  short int y = 513;
  int z = 128;
  short int* ptrX = &x;
  short int* ptrY = &y;
  int* ptrZ = &z;

  printf("%p\n", ptrX);
  printf("%p\n", ptrY);
  printf("%p\n", ptrZ+1);

  return 0;
}
```

`ptrZ+1` akan menuju ke alamat yang sama dengan `ptrY`, karena `ptrZ+1` melompati 4 byte dari pointernya (alamat memori `z`).

Apa yang terjadi jika `ptrZ+2`?, kita akan membuat pointer `ptrZ` melompati 2 kali 4 byte dari pointernya (alamat memori `z`).

{{< img name=img02 size=small >}}

`ptrZ+2` menuju alamat sesudah `ptrX`, dikarenakan ini membuat `ptrZ` melompati 8 bytes, bukan menuju alamat blok memori `ptrX`.

Ubah tipe data `z` menjadi `short int`, maka `ptrZ+2` akan melompati 2x2 byte dari alamat pointernya.

```c
#include <stdio.h>

int main() {
  short int x = 1026;
  short int y = 513;
  short int z = 128;
  short int* ptrX = &x;
  short int* ptrY = &y;
  short int* ptrZ = &z;

  printf("%p\n", ptrX);
  printf("%p\n", ptrY);
  printf("%p\n", ptrZ+2);

  return 0;
}
```

Ini juga merupakan alasan mengapa array hanya bisa menyimpan tipe data sejenis.
