---
title: Char dan String Literal
date: 2024-04-23
weight: 4
tags: 
  - C
---

Sebuah "string" di C adalah sebuah array yang terdiri atas kumpulan `char`. Mereka dibedakan melalui literal.

## Char literal

Char literal ditandai dengan `' '` tanda petik satu, untuk membungkus sebuah karakter.

```c
char x = 'X';
```

## String literal

Sementara string literal ditandai dengan tanda petik dua `" "`, untuk membungkus banyak karakter dalam sebuah array.

```c
char greeting[] = "Hello world";

printf("This is also enclosed by a string literal");
```