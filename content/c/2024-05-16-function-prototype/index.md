---
title: Function prototype
date: 2024-05-16
weight: 15
tags: 
  - C
---

Function prototype, sesuai namanya membuat compiler agar tau fungsi apa saja yang akan dipanggil beserta return type dan juga parameternya.

Function prototype wajib dideklarasikan jika fungsi dibuat sesudah main function (memang sebaiknya seperti itu). Opsional jika fungsi dibuat sebelum main function.

Bentuk deklarasi, dibawah akan membuat compiler bahwa kode akan mengeksekusi fungsi yang tidak akan `return` sebuah nilai, dengan 2 parameter secara berurut: tipe data`int` dan sebuah string (array of `char`):

```c
void persegi(int sisi, char nama[]);
```

Jadi, contoh lengkapnya seperti ini:
```c
#include <stdio.h>

void persegi(int sisi, char nama[]);
double lingkaran(double r);

int main () {
  persegi(10, "Merca");

  printf("Luas lingkaran: %lf\n", lingkaran(13.3));
  return 0;
}

void persegi (int sisi, char nama[]) {
  sisi *= sisi;
  printf("Luas persegi %s adalah: %d\n", nama, sisi);
}

double lingkaran (double r) {
  return 3.14 * r * r;
}
```