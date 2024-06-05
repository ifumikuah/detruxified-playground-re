---
title: Function pointer
date: 2024-06-04
weight: 18
tags:
  - C
---

Fungsi yang me-return sebuah pointer berbeda dengan pointer dari sebuah fungsi. Jika Pointer return function adalah fungsi yang return sebuah pointer, maka function pointer adalah sebuah pointer yang menuju alamat dari fungsi tersebut.

Deklarasi function pointer:

```c
int (*ptrf)(int, int) = &func;
```

Diatas akan membuat pointer `ptrf` yang merupakan pointer dari fungsi `int` dengan dua parameter `int` dan `int`.

## Callback functions

Implementasi dari function pointers salah satunya adalah callback functions. Callback functions adalah dimana sebuah fungsi menjadi argument sebuah fungsi.

Pertama, kita harus membuat fungsi utamanya, yang menampung fungsi sebagai argument.

```c
// Prototype
int mfunc(int n, void (*cb)(int));
```
```c
int mfunc(int n, void (*cb)(int)) {
  (*cb)(n);
  return n;
}
```

Fungsi diatas akan mengeksekusi fungsi yang dipanggil sebagai callback (singkatnya mengeksekusi callback), lalu return integer yang dimasukkan sebagai parameter.

```c
void (*cb)(int)
```

Fungsi callback `cb` berupa pointer dari fungsi yang return nilai `void` dengan satu argument `int`.

Lalu kita akan membuat fungsi yang akan dijadikan callback.

```c
// Prototype
void call(int n);
```
```c
void call(int n) {
  printf("Hello! x%d \n", n);
}
```

Kode callback self explanatory, mencetak *Hello* lalu disertai `n` kali disaut.

Di fungsi `main()` kita harus membuat pointer untuk fungsi `call`, karena yang diminta oleh `mfunc` adalah pointer/alamat dari fungsi tersebut.

```c
int main() {
  int x = 9; // jumlah n
  void (*cbf)(int) = &call; // Pointer menuju alamat fungsi callback call

  return 0;
}
```

Lalu kita akan memanggil `mfunc()` beserta callbacknya.

```c
#include <stdio.h>
#include <stdlib.h>

void call(int n);
int mfunc(int n, void (*cb)(int));

int main() {
  int x = 9;
  void (*cbf)(int) = &call;

  printf("Shout times: %d\n", mfunc(x, cbf));

  return 0;
}

int mfunc(int n, void (*cb)(int)) {
  (*cb)(n);
  return n;
}

void call(int n) {
  printf("Hello! x%d \n", n);
}
```