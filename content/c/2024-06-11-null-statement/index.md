---
title: Null statement
date: 2024-06-11
weight: 33
tags:
  - C
---

Bayangkan sebuah skenario, kita ingin membuat program yang menghitung total karakter yang dimasukkan.

```c
#include <stdio.h>

main()
{
  size_t nc;
  nc = 0;

  while (getchar() != '\n')
    nc++;

  printf("%d\n", nc);
  return 0;
}
```

Kunci dari program ini berada di `nc++`. Dimana `nc = nc + 1` disaat sebuah karakter dimasukkan, setelahnya perulangan akan berhenti disaat user menekan karakter newline `\n` biasanya tombol 'enter'.

Selain while, kita juga bisa menggunakan `for` loop, sebuah perulangan menggunakan `for` loop mengharuskan didalam bloknya/*body* nya diisi oleh sesuatu yang dieksekusi saat perulangan.

Tetapi jika kita memakai `for` loop untuk program ini, semua statement yang diperlukan sudah ada di bagian inisialisasi/*initialization* `for` loop itu sendiri.

```c
for(nc = 0; getchar() != '\n'; nc++);
```

Jadi apakah kode diatas bisa dieksekusi? jawabannya masih bisa, juga tidak ada *issue* sama sekali terhadap kode diatas.

```c
#include <stdio.h>

int main() {
  size_t nc;

  for(nc = 0; getchar() != '\n'; nc++);

  printf("chars entered: %d\n", nc);
  return 0;
}
```

Tetapi *syntactic convention* dari `for` loop mengharuskan dirinya diberi statement didalam bodinya. Kita bisa menggunakan *null statement* dengan memindahkan semikolon `;` diujung `for` sebagai akhir dari statement ke bagian bodinya.

```c
#include <stdio.h>

int main() {
  size_t nc;
  for(nc = 0; getchar() != '\n'; nc++)
    ;
  printf("chars entered: %d\n", nc);
  return 0;
}
```

Posisi didalam blok `;` seperti diatas memberi tau pada orang lain kalau tidak ada statement yang perlu dijalankan di dalam `for` loop.