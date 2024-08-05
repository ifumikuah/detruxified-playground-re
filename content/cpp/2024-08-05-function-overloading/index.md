---
title: Function Overloading
date: 2024-08-05
weight: 5
tags:
  - C++
---

Function overloading adalah implementasi dari *polymorphism* di C. Ini adalah fitur dimana fungsi dengan nama yang sama dapat menerima argument yang berbeda.

Function overloading dihitung dari nama fungsi dan jenis/jumlah argument yang bisa diterima.

Misal:

```cpp
int mul(int n1, int n2)
{
  return n1 * n2;
}

double mul(double n1, double n2)
{
  return n1 * n2;
}
```

Dua fungsi `add` diatas termasuk function overloading.

Namun, dua fungsi tersebut tidak boleh hanya mengandung `return` type yang berbeda, karena menyebabkan ambiguitas kepada kompiler:

```c
float divs(int n1, int n2)
{
  return (float) n1 / n2;
}

int divs(int n1, int n2)
{
  return n1 / n2;
}
```

Dua atau lebih fungsi (nama yang sama) dengan return berbeda dan parameter yang sama akan menyebabkan ambiguitas.

Namun, jika seperti ini:

```c
float divs(int n1, int n2)
{
  return (float) n1 / n2;
}

int divs(int n1, int n2, int n3)
{
  return n1 / n2 + n3;
}
```

Return type beda dan tipe data yang sama tentu menyebabkan ambiguitas. Namun terdapat perbedaan jumlah parameter salah satu fungsi. Kasus seperti ini termasuk kedalam kualifiasi function overloading.

Karena fungsi akan memenuhi syarat function overloading jika:

- Nama dua/lebih fungsi sama.

Dan, salah satu dari syarat dibawah terpenuhi:

- Tipe data parameter yang berbeda.
- Jumlah parameter yang berbeda.

