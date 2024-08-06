---
title: Array dan String di C++
date: 2024-08-06
weight: 10
tags:
  - C++
---

Deklarasi array bisa menggunakan dua cara: Container (dari class) atau Primitives (cara klasik).

## Containers

Array yang di declare dari class. Memiliki behavior yang sama dengan array primitive (C style). Namun array ini tidak dievaluasi sebagai pointer.

Jadi tipe data array ini bukanlah pointer.

```cpp
std::array<int, 6> nums = {4, 1, 2, 5, 6, 3};
```

## Primitives

Array yang dideklarasi dengan C-style, memiliki behavior seperti biasanya dan dievaluasi sebagai pointer.

```cpp
int nums[6] = {4, 1, 2, 5, 6, 3};
```

## String

String class memiliki behavior yang mirip dengan array class, dimana di string class memiliki beberapa method identik dengan array, [lihat artikel ini](../2024-08-06-array-method/).

String ini juga dapat diassign layaknya tipe data primitives, dimana string primitive (char pointer) tidak bisa melakukan hal ini.

```cpp
std::string str1 = "Cats";
std::string str2;

str2 = str1;

std::cout << str2 << std::endl;
```