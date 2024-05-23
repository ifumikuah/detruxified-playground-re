---
title: Structs
date: 2024-05-23
weight: 24
tags:
  - C
---

Typedef adalah keyword untuk memberi *alias* terhadap tipe data dari variable yang ingin kita deklarasikan.

```c
#include <stdio.h>

typedef unsigned long int longint;

int main() {
  longint angka = 200;

  printf("%lu", angka);
  return 0;
}
```

## Menggunakan typedef pada struct

Deklarasikan struct dengan `typedef` didepannya.

```c
typedef struct Employee
{
  char name[15];
  int age;
} emp;
```

Struct tersebut memiliki alias `emp`.

```c
int main() {
  emp jonas = {"Jonas", 22};
  emp rick;

  strcpy(rick.name, "Rick");
  rick.age = 20;

  printf("%s, %d\n", rick.name, rick.age);
  return 0;
}
```