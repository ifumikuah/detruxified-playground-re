---
title: Aritmethic unary operator
date: 2024-07-07
weight: 35
tags:
  - C
---

`++` dan `--` dikenal sebagai unary operator yang hanya membutuhkan satu operand, umumnya banyak orang sekedar mengetahui menambah/kurang sebanyak satu dari nilai variable.

## Details

```c
int x = 4;
```

Menulis `x++` sama dengan: 

```
x = x + 1
```

`x--` atau `x++` adalah post-fix, artinya variable diselesaikan terlebih dahulu sebelum ditambah 1.

Lalu untuk pre-fix, variable operand ditambah 1 terlebih dahulu sebelum diselesaikan.

```
++x => x = (1 + x);
```

*Consider:*

```c
int x = 4;
int* px = &x
```

```
apa artinya: 
++*px => *px = *(px + 1) => Garbage Value
*px++ => *px = (*px) + 1 => Nilai px+1
```

`++*px` menambah 1  blok memory untuk `px` lalu melakukan dereference terhadap `px` (pre-incremental). Sedangkan, `*px++` dereference `px` terlebih dahulu kemudian menambah satu nilai didalam `px` tersebut.

## Lvalue

Unary operator mengharuskan operand adalah sebuah `lvalue`. Lvalue adalah sebuah nilai yang memiliki alamat.

*Consider*

```c
int a = 5;
int b = 3;
```

Statement `a+b` bukan sebuah `lvalue` karena evaluasi keduanya tidak memiliki memori yang di *assign* untuk menampungnya. Namun, statement tadi bisa menjadi sebuah `lvalue` jika di assign ke sebuah variable:

```c
int sum = a+b;
```

`sum` adalah sebuah `lvalue`.

Unary Operator hanya menerima `lvalue` sebagai operandnya.

```
a++ // benar
a = a + 1

(a+b)++ // salah, a+b tidak memiliki memory yang menampung hasilnya
(a+b) = (a+b) + 1
```