---
title: Array swap
date: 2024-05-22
weight: 22
tags:
  - C
---

Melakukan swap tipe data seperti int, float atau char sangat mudah dilakukan.

```c
int a = 12;
int b = 36;

int temp = a;
a = b;
b = temp;
```

Bagaimana jika ingin melakukan swap tipe data array ?, swap array dengan cara diatas tidak bisa dilakukan, yang bisa dilakukan adalah dengan menggunakan `strcpy()` dari library `string.h`.

```c
char a[5] = "red";
char b[5] = "blue";
char temp[5];
```

Yang dilakukan selanjutnya adalah melakukan `strcpy()` untuk memindahkan `a` ke `temp`.

```c
strcpy(temp, a);
```

Ingat bahwa argumen pertama adalah argumen destinasi, dan kedua adalah argumen sumber.

Lalu tukar `a` menjadi `b` dan `b` menjadi `temp`.

```c
strcpy(a, b);
strcpy(b, temp);
```

Hasil

```c
char a[5] = "red";
char b[5] = "blue";
char temp[5];

strcpy(temp, a);
strcpy(a, b);
strcpy(b, temp);
```
