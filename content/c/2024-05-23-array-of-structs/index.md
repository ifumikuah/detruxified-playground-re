---
title: Array of structs
date: 2024-05-23
weight: 25
tags:
  - C
---

Membuat array of structs, sebuah array yang di isi structs.

```c
#include <stdio.h>
#include <string.h>

typedef struct Employee
{
  char name[15];
  int age;
} emp;

int main() {
  emp jonas = {"Jonas", 23};
  emp lamar = {"Lamar", 25};
  emp jason = {"Jason", 21};
  emp timothy = {"Timothy", 27};

  emp emps[] = {jonas, lamar, jason, timothy};
  int length = sizeof(emps) / sizeof(emps[0]);

  for (int i = 0; i < length; i++)
  {
    printf("%s\t%8d\n", emps[i].name, emps[i].age);
  }
  

  return 0;
}
```

Jika tidak menggunakan typedef: 

```c
#include <stdio.h>
#include <string.h>

struct Employee
{
  char name[15];
  int age;
};

int main() {
  struct Employee jonas = {"Jonas", 23};
  struct Employee lamar = {"Lamar", 25};
  struct Employee jason = {"Jason", 21};
  struct Employee timothy = {"Timothy", 27};

  struct Employee emps[] = {jonas, lamar, jason, timothy};
  int length = sizeof(emps) / sizeof(emps[0]);

  for (int i = 0; i < length; i++)
  {
    printf("%s\t%8d\n", emps[i].name, emps[i].age);
  }

  return 0;
}
```