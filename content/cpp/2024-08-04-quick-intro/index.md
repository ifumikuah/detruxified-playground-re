---
title: Quick Intro
date: 2024-08-04
weight: 1
tags:
  - C++
---

C++ adalah C dalam varian OOP dengan tambahan sintaks baru, mempersulit hidup anda sekaligus mempermudah hidup orang.

Basic nya C++ mirip dengan C, akan tetapi C++ memperkenalkan operator dan keyword baru.

## Basic Data Types

Deklarasi dan assignment variable sama dengan C.

```cpp
int intd;
intd = 11;

int integ = 8;
```

```cpp
float fltd;
fltd = 11.69;

double integ = 8.1123;
```

```cpp
char chr;
chr = 'A';

char ltr = 'B';
```

Tidak perlu header lagi untuk deklarasi tipe data `bool`.

```cpp
bool isit;
isit = true;

bool nah = false;
```

## Print

Untuk mencetak, kita menggunakan fitur terbaru dari C yang ada di header `iostream`. Header `iostream` ini mirip dengan `stdio` di C, sama-sama berurusan dengan STDIN/STDOUT.

```cpp
std::cout << "Hello Babayo!";
```

`std` adalah sebuah namespace yang nanti dibahas di artikel selanjutnya. Simpelnya namespace `std` ini adalah sebuah scope. Jadi kita menggunakan `cout` yang ada dalam `std`.

`cout` berasal dari header `iostream`.

`<<` adalah semacam input redirection, jadi data berupa `"Hello Babayo!"` akan diarahkan ke `cout` ini untuk dproses oleh routine tersebut untuk di output ke STDOUT.