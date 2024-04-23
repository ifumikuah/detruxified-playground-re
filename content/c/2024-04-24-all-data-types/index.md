---
title: Semua data types
date: 2024-04-23
weight: 4
tags: 
  - C
---

Ada 5 tipe data utama di C: `char`, `int`, `float`, `double` dan `boolean`.

`boolean` adalah nilai true/false yang berguna untuk logika, tipe data ini hanya memiliki besar 1 bit karena hanya memuat true: `1` atau false: `0`.

## Modifier

Selain itu ada 4 modifier untuk setiap data type nya (hanya berlaku untuk `char`, `int`, `float`dan `double`).

Modifier ini adalah `long`, `short`, `signed` dan `unsigned`.

### long dan short

Ini mengacu pada kapasitas size dari value itu sendiri. Perlu diketahui ini hanya berlaku untuk tipe data numerik `int` dan `float` atau `double`

Berikut tabelnya. Range adalah seberapa besar nilai yang bisa ditampung.

| Type | Size | Range |
|-|-|-|
| `short` | 16 bit | `−32767`, `32767` |
| `long` | 32 bit | `−2147483647`, `2147483647` |
| `long long` | 64 bit | `−9223372036854775807`, `9223372036854775807` |

Angka yang kebesaran tidak bisa menampung diluar kapasitas, jika terjadi, maka value nya akan kembali berputar lagi dari nilai minimum.

Contoh: Apa yang terjadi jika kita memberikan nilai yang berlebih untuk `short int`? Maka nilainya akan mundur lagi dari range minimum.

```c
#include <stdio.h>

int main()
{
  short int val = 32770;
  printf("val is: %hi", val);

  return 0;
}
```
```plain
val is: -32766
```

### signed dan unsigned

Value yang ditampung akan selalu positif atau tidak.

Kita beri contoh untuk `int`:

Defaultnya `int` memiliki modifier `short` dan `signed`. Ini artinya `int` bisa menampung value sebesar 16 bit, dimulai dari `−32767` sampai `32767`.

Namun apa yang terjadi jika itu `unsigned int`?

`unsigned int` bisa menampung value sebesar 16 bit, namun nilai nya positif. Ini artinya dimulai dari `0` sampai `65535`.

`signed` dan `unsigned` berlaku untuk `char`, `int`. Namun tidak untuk `float` dan `double`.

## Chart

Berikut chart lengkapnya.

| Type | Bit | Format specifier | Range keyword |
|-|-|-|-|
| `char` | 8 | `%c` | `[CHAR_MIN, CHAR_MAX]` |
| `signed char` | 8 | `%c` | `[SCHAR_MIN, SCHAR_MAX]` |
| `unsigned char` | 8 | `%c` | `[0, UCHAR_MAX]` |
| `short`<br>`short int`<br>`signed short`<br>`signed short int` | 16 | `%hi`/`%hd` | `[SHRT_MIN, SHRT_MAX]` |
| `unsigned short`<br>`unsigned short int` | 16 | `%hu` | `[0, USHRT_MAX]` |
| `int`<br>`signed`<br>`signed int` | 16 | `%i`/`%d` | `[INT_MIN, INT_MAX]` |
| `unsigned`<br>`unsigned int` | 16 | `%u` | `[0, UINT_MAX]` |
| `long`<br>`long int`<br>`signed long`<br>`signed long int` | 32 | `%li`/`%ld` | `[LONG_MIN, LONG_MAX]` |
| `unsigned long`<br>`unsigned long int` | 32 | `%lu` | `[0, ULONG_MAX]` |
| `long long`<br>`long long int`<br>`signed long long`<br>`signed long long int` | 64 | `%lli`/`%lld` | `[LLONG_MIN, LLONG_MAX]` |
| `unsigned long long`<br>`unsigned long long int` | 64 | `%llu` | `[0, ULLONG_MAX]` |
| `float` |  | `%[fgea]` or `%[FGEA]` |  |
| `double` |  | `%l[fgea]` or `%l[FGEA]` |  |
| `long double` |  | `%L[fgea]` or `%L[FGEA]` |  |

{{< hint type="note" title="Hint" >}}
Format specifier pada `float`, `double` dan `long double` dibaca dengan notasi regex. Misal untuk `double`: `%lf`, `%lg`, `%lA` dan seterusnya.
{{< /hint >}}

