---
title: Float dan double
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

Namun, seperti yang ada di output CLI kamu, decimal point tersebut bisa menampung sampai enam digit panjangnya (32 bit).

## Double

Jika menurutmu `float` kurang presisi untuk kebutuhanmu, `double` menawarkan 15-17 decimal points (64 bit).

```c
int main()
{
  float pi = 3.141592653589;
  double dpi = 3.141592653589;
  printf("pi is: %f", pi);
  printf("pi is: %lf", dpi);

  return 0;
}
```

Tidak ada bedanya 🤔.

Perbedaan terlihat saat mantissa/floating point di perlebar digitnya.

```c
int main()
{
  float pi = 3.141592653589;
  double dpi = 3.141592653589;
  printf("pi is: %0.12f", pi);
  printf("pi is: %0.12lf", dpi);

  return 0;
}
```

Bisa dilihat kalau `float` kehilangan akurasinya di digit ke 7.