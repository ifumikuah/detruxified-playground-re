---
title: Array of structs
date: 2024-07-07
weight: 41
tags:
  - C
---

Membuat sebuah array yang berisikan structs.

Pertama membuat sebuah typedef untuk struct *tagname* `species` dengan alias `cat`.

```c
#include <stdio.h>

typedef unsigned short int shortnum;
typedef struct species
{
  char name[12];
  shortnum age;
} cat;

int main() {
	
	return 0;
}
```

Atau juga bisa membuat nya tanpa `typedef`. Tetapi harus define `struct tagname` untuk menggunakannya. *a tedious task it is*

```c
...
	struct species kittyfield[n];
...
```

Sekarang untuk kasus menggunakan `typedef`. Define struct baru dengan alias `cat`. `cat` adalah alias dari sebuah `struct species`.

```c
int main() {
	shortnum members = 3;
	cat kittyfield[members];
}
```

Sekarang waktunya mengisi member dan umur untuk setiap anggota `kittyfield`.

```c
for (size_t i = 0; i < visitor; i++)
{
  printf("enter member #%d name: ", i+1);
  scanf("%s", kittyfield[i].name);
  printf("enter member #%d age: ", i+1);
  scanf("%d", &kittyfield[i].age);
  printf("\n");
}
```

Gunakan operator dot `.` untuk mengakses *member* didalam struct, sebuah variable yang ada di struct disebut dengan *member*.

```c
typedef struct species
{
  char name[12]; // -> member
  shortnum age; // -> member
} cat;
```

Lalu print semua member dari array `kittyfield`.

```c
for (size_t i = 0; i < visitor; i++)
{
  printf("member #%d: %s, %d\n", i+1, kittyfield[i].name, kittyfield[i].age);
}
```