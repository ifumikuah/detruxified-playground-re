---
title: Quick Intro
date: 2024-04-23
weight: 1
tags: 
  - C
---

Selamat datang di C

Comment di code

```c
#include <stdio.h>

int main() {
  // Ini adalah comment

  /* 
    Ini adalah
    Multi line 
    comments   
  */

  return 0
}
```

## Return 0

`return 0` ini adalah tidak wajib, hanya sebuah common convention yang disarankan, agar kode tahu berapa exit status jika kode berjalan dengan baik.

Dengan kata lain, memberi tahu kapan kode harus selesai.

## Variabel

Saat ini, kita harus mengenal 2 tipe data yang lebih sering dipakai. Walaupun ada banyak tipe data disini, untuk saat ini kita diperkenalkan dengan: `int` dan `char`

- `int` menyimpan sebuah integer, angka bilangan integer (`3.14` termasuk desimal point, bukan integer)
- `char` menyimpan sebuah karakter ASCII, misal: `'A'`

Ada berbagai cara inisialisasi dan deklarasi variable:

```c
int main() {
  int num; // Inisialisasi
  num = 12; // Deklarasi

  int three = 3 // Init + Declare

  char req, grade; // Multiple variable init
  req = 'A';
  grade = 'C';
}
```

## Import header

Header adalah ibaratnya modul di C, memperbolehkan sebuah file digunakan oleh file lain untuk tujuan modularitas.

Sebelum kita ingin mencetak sesuatu di CLI, header `stdio.h` harus di include dulu, dipaling atas.

```c
#include <stdio.h>

int main() {

}
```

## Print dan format specifier

Kita asumsikan `stdio.h` sudah ter-include.

```c
int main () {
  printf("Hallo pendatang!")
}

```

Lalu compile & run code!

### Format specifier

Format specifier adalah seperti templating yang harus diletakkan jika ingin mencetak sebuah variable.

```c
int main () {
  int day = 5;
  char unnamed = 'X';

  printf("Hallo Tuan %c!, hari ini adalah hari ke %d kamu bekerja", unnamed, day)
}

```
Sekarang kamu harus compile & run code diatas!

Perhatikan bagaimana `unnamed` dan `day` bisa cocok urutannya!. Di penghujung output terdapat variable yang "disematkan", secara berurutan: `unnamed` dan `day`.

Peletakkannya harus sesuai urutan agar output yang diberikan juga sesuai.

Lalu apa itu `%c` dan `%d`?, Keduanya itu yang disebut dengan *Format specifier*. Huruf ini bukan sebarang huruf, harus sesuai dengan tipe data yang diberikan, untuk saat ini kita masih mempelajari 2 tipe data:

|Tipe data|Format specifier|
|-|-|
| `int` (integer) | `%d` |
| `char` (character) | `%c` |

