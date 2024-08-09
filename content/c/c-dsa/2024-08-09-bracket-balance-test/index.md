---
title: "Bracket balance check: stack"
date: 2024-08-09
description: "Stack"
tags: [teknologi, c]
---

Balanced bracket adalah salah satu pertanyaan interview yang sering ditanyakan, tujuan algoritma ini adalah untuk mencari apakah bracket seimbang atau tidak.

Bayangkan ada sebuah notasi dengan bracket:

```
(21*31) + (45*(8/2))
```

Dari notasi diatas, sebuah program harus memastikan apakah pasangan bracket cocok atau tidak.

```
(21*31) + ((45*(8/2))
```

Jika tidak, maka error akan terjadi.

## Algoritma

Untuk merealisasi routine ini, kita memanfaatkan [stack](../2024-08-03-stack-intro/). Idenya adalah menumpukkan opening bracket ke stack, jika closing bracket ditemukan, maka harus dicocokkan dengan stack topnya. Seperti ini outlinenya:

1. Iterate karaker ke karakter
2. Karakter pertama harusnya opening bracket, masukkan kedalam stack (`push`).
3. Masukkan setiap opening bracket kedalam stack.
4. Jika closing bracket ditemukan, pastikan closing tersebut cocok dengan pasangannya yang ada di stack paling atas dengan `peek`.
5. Jika cocok, `pop` opening bracket tersebut dari stack, membuat stack berkurang.
6. Sebaliknya, jika pasangan bracket tidak cocok, maka stack akan 'terpolusi' dengan cara closing tersebut di `push` kedalam stack.
7. Stack yang terpolusi membuat iterate karakter selanjutnya berantakan.
8. Hal yang sama untuk closing bracket selanjutnya sampai stack kosong.
9. Jika stack kosong, maka string tersebut balance.

## Mempersiapkan stack

Pembuatan stack, sudah dijelaskan di artikel [sebelumnya](../2024-08-03-stack-intro/).

```c
typedef struct Stack
{
  char array[24];
  int size;
} Stack;

void push(Stack* stack, char value)
{
  stack->size++;
  stack->array[stack->size] = value;
}

void pop(Stack* stack)
{
  if (stack->size < 0)
    return;

  stack->size--;
}

char peek(Stack* stack)
{
  return stack->array[stack->size];
}

bool isempty(Stack* stack)
{
  return stack->size < 0;
}
```