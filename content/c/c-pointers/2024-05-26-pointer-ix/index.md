---
title: Call by reference
date: 2024-05-26
weight: 9
tags:
  - C
---

Bagaimana cara kita memanipulasi variable yang ada di main function menggunakan user defined function.

```c
#include <stdio.h>

void adder(int numb, int toAdd);
int main() {
  int x = 100;

  adder(x, 10);
  printf("incremented value of x: %d\n", x);
  return 0;
}
void adder(int numb, int toAdd) {
  numb += toAdd;
}
```

Jika kode diats dicoba, `x` tidak berubah menjadi `110`. Karena `x` yang diterima oleh `adder()` disaat pemanggilannya bukanlah `x` yang sama dengan deklarasi main function. Pemanggilan ini disebut *call by value*.

```c
adder(x, 10);
```

Yang terjadi adalah, value `x` yang diterima saat pemanggilan dimap ke variable sementara didalam fungsi adder yaitu disimpan didalam `numb`.

`numb` yang menyimpan value `x` tadi ini hanya hidup sementara sesaat function berjalan, dan hilang disaat blok function sudah tereksekusi sepenuhnya.

## Solusi

Bagaimana solusinya agar `x` berubah? salah satunya cara adalah menggunakan alamat memori `x` sebagai argument, atau disebut juga pointer as argument.

Pertama deklarasi fungsi prototype.

```c
void adder(int* numb, int toAdd);
```

```c
#include <stdio.h>

void adder(int* numb, int toAdd);

int main() {
  int x = 100;

  adder(&x, 10);
  return 0;
}

void adder(int* numb, int toAdd) {
  *numb += toAdd;
}
```

pointer `numb` akan menampung alamat dari `x`, oleh karena itu kita harus passing memori dari `x` sebagai argumen di pemanggilan.

```c
adder(&x, 10);
```