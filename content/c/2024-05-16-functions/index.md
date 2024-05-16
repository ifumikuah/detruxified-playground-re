---
title: Functions
date: 2024-05-16
weight: 14
tags: 
  - C
---

Membuat fungsi di C

```c
#include <stdio.h>

void panggil_fungsi () {
  printf("Eksekusi dan return hasil fungsi!");
}

int main () {
  panggil_fungsi();
  return 0;
}
```

## Parameters

Fungsi

```c
void persegi (int sisi) {
  sisi *= sisi;
  printf("Luas persegi adalah: %d\n", sisi);
}
```

deklarasi parameter sama seperti deklarasi variable, memberikan `int sisi` sebagai expected value / nilai tipedata yang diharapkan.

Lalu panggil dengan: 
```c
persegi(40);
// Atau
const int Panjang_sisi = 12;
persegi(Panjang_sisi);
```

### Menambah parameter (lebih dari satu parameter)

```c
void persegi (int sisi, char nama[]) {
  sisi *= sisi;
  printf("Luas persegi %s adalah: %d\n", nama, sisi);
}
```
```c
persegi(40, "Kecil");
```

## Return

Specify return value di awal deklarasi fungsi.

```c
double lingkaran (double r) {
  return 3.14 * r * r;
}
```

Maka nilai yang direturn haruslah `double`.
```c
const double luas = lingkaran(3.38)
```

Pemanggilan secara langsung:
```c
printf("Luas lingkaran: %lf\n", lingkaran(13.3));
```