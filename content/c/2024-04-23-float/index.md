---
title: Float
date: 2024-04-23
weight: 2
tags: 
  - C
---

Selain `int` dan `char` tadi, mari berkenalan dengan sebuah tipe data: `float`.

Tipe data ini memiliki purpose akurasi sebenarnya, yaitu adalah dengan memberi titk koma atau *decimal point*.

Seperti tipe data sebelumnya, format specifier dari tipe data ini adalah `%f`

```c
int main () {
  float pi = 3.14;

  printf("Number of a pi is: %f", pi)
}
```
```plain
Number of a pi is: 3.140000
```

Namun, seperti yang ada di output CLI kamu, decimal point tersebut bisa menampung sampai enam digit panjangnya.