---
title: Artihmetic operators
date: 2024-04-24
weight: 8
tags: 
  - C
---

Seperti bahasa pemrogamman umumnya, `C` sudah pasti memiliki operator aritmatik.

| Operator | Operasi |
|-|-|
| `+` | Tambah |
| `-` | Kurang |
| `*` | Perkalian |
| `/` | Pembagian |
| `%` | Modulo (sisa bagi) |

```c
#include <stdio.h>

int main()
{
  const short int operand1 = 5;
  const short int operand2 = 2;

  const short int res = operand1 + operand2;

  printf("%d", res);

  return 0;
}
```

## Pembagian

Untuk pembagian, jika pembagian masih menyisakan angka, maka pembagian akan menghasilkan integer nya saja (dalam keadaan dibulatkan kebawah).

```c
const short int operand1 = 5;
const short int operand2 = 2;

const short int res = operand1 / operand2;

printf("%d", res);
```
```plain
2
```

Ada baiknya kamu casting (konversi) `int` menjadi `float` atau `double` jika ingin melakukan sebuah operasi pembagian.

## Operasi dengan tipe data float

```c
const short int operand1 = 3;
const float operand2 = 1.25;

const float res = operand1 * operand2;

printf("%f", res);
```
```plain
3.750000
```

## Increment dan decrement

Menambah/mengurangi value didalam variable tersebut sebanyak 1, tidak berlaku untuk `const`.

```c
int num = 5;
num++;

printf("%d", num); // 6
```
```c
int num = 5;
num--;

printf("%d", num); // 4
```

## Augmented assigment

Ini sama seperti increment/decrement, bedanya value bisa ditambah selain sebanyak 1.

```c
int num = 5;
num += 5;

printf("%d", num);
```

```c
int num = 40;
num -= 5;

printf("%d", num);
```

```c
int num = 5;
num *= 5;

printf("%d", num);
```

```c
float num = 40;
num /= 5;

printf("%f", num);
```