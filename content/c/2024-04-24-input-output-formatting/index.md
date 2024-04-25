---
title: Input output formatting
date: 2024-04-25
weight: 6
tags: 
  - C
---

Formt specifier `%`, selain digunakan untuk tipe data yang sesuai, kamu juga bisa memberi format tertentu dengan meletakkan simbol/angka diantara `%` specifier dan tipe datanya.

## Mengatur digit pada floating point

Gunakan dengan format

```plain
%.x
```

dimana `x` adalah batasan digit tersebut.

```c
// Membatasi decimal point pada pi
double pi = 3.1415926535;
printf("angka pada pi: %.2lf", pi);
```

## Minimum field width

Mengatur yield/spasi minimal pada output.

Misal:

```plain
xx123456
xxxx1234
xxxxx123
```

Tiga baris diatas memiliki 8 yield/spasi minimal.

Bagaimana cara implementasi di C:

```c
int main()
{
  int arch = 32;
  double pi = 3.1415926535;
  char letter = 'V';

  printf("%8.2lf\n", pi);
  printf("%8c\n", letter);
  printf("%8d", arch);

  return 0;
}
```
```plain
    3.14
       V
      32
```

## Align left

`-` mengubah align-nya menjadi dari kiri.

```c
int main()
{
  int arch = 32;
  double pi = 3.1415926535;
  char letter = 'V';

  printf("%8.2lf\n", pi);
  printf("%-8c\n", letter);
  printf("%8d", arch);

  return 0;
}
```
```plain
    3.14
V       
      32
```