---
title: "Function templates"
date: 2024-08-07
weight: 13
tags: [C++]
---

`template` adalah keyword di C++ untuk mengatasi redundancy fungsi yang kita definisi.

Bayangkan harus menduplikat definisi fungsi overloaded yang sama hanya karena tipe data yang berbeda.

```cpp
// integer
int add(int n1, int n2)
{
  return n1 + n2;
}

// double
double add(double n1, double n2)
{
  return n1 + n2;
}

// char
char add(char n1, char n2)
{
  return n1 + n2;
}
```

Dengan `template` kita bisa mengeleliminasi redundancy dari overload ini:

```cpp
template <typename T> T add(T n1, T n2)
{
 return n1 + n2;
}
```

`T` adalah naming convention untuk template tipe data sejenis pada fungsi tersebut. Prototype fungsi akan seperti ini:

```cpp
template <typename T> T add(T, T);
```

Panggil fungsi dengan tipe data secara eksplisit:

```c
main()
{
  int sum = add<int>(1, 1);
}
```

Diatas, `T` pada panggilan tersebut menjadi `int`.

Secara implisit:

```c
main()
{
  int sum = add(1, 1);
}
```

Diatas, kompiler tau sendiri tipe data yang akan dipakai berdasarkan parameter dan tipe data saat deklarasi variabel.

Namun, jika deklarasi seperti ini:

```c
main()
{
  int sum = add(1.6, 1.5);
}
```

`add` akan return sebuah double (berdasarkan ketentuan definisi), lalu *casting* nilai tersebut ke integer, mengubah nilai `3.1` (double) menjadi `3` (integer).

## Dua tipe data

Kita bisa memberikan lebih dari satu jenis tipe data pada template.

```cpp
template <typename T, typename U> T add(T n1, U n2)
{
  return n1 + n2;
}
```

Namun, return type akan menjadi ambigu ketika kita melakukan panggilan.

```cpp
add(3, 3.3);
```

Kompiler akan mengidentifikasi tipe data yang cocok berdasarkan valuenya, dan assign tipe data tersebut sebagai `T` atau `U`.

Berdasarkan deklarasi diatas, maka output adalah sebuah integer dan hal ini tidak kita inginkan. Hal yang bisa dilakukan untuk menyelesaikan masalah ini adalah dengan keyword `auto`.

```cpp
template <typename T, typename U> auto add(T n1, U n2)
{
  return n1 + n2;
}
```

Kompiler akan menentukan (dengan pintar) tipe data yang akan keluar berdasarkan promosi. Jika tipe data tertinggi ditemukan (dalam panggilan ini float adalah tipe paling tinggi) maka output berupa tipe data tinggi tersebut.