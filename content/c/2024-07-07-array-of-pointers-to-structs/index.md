---
title: Array of pointers to structs
date: 2024-07-07
weight: 42
tags:
  - C
---

Membuat sebuah array yang isinya pointer to sebuah struct. Membuat nya sama seperti membuat array yang isinya pointer to strings of char;

Array of pointer to strings of chars:

```c
char* name = "Haikal" // Pointer to strings of chars
char* team[] = {"Jody", "Mark", "Buz"} // Array of Pointers to strings of chars
```

Membuat Array of pointers to structs:

```c
typedef struct species
{
  char name[12];
  shortnum age;
} cat;

int main() {
	cat* kittyland[5];
}
```

Diatas membuat sebuah array dari 5 buah pointer ke structs (array of pointers to structs). Jadi setiap element array adalah sebuah pointer menuju sebuah struct bertipe data `struct species`.

## Akses pointer to struct

Dalam konteks pointer to struct, kamu menggunakan operator `->` untuk mengakses sebuah pointer struct.

```c
int main() {
	cat* garfield;
	garfield->name = "Garfield";
	garfield->age = 13;
}
```

Sama halnya dengan pointer to struct jika itu merupakan element dari sebuah array.

```plain
structname[n]->member
```

```c
typedef struct species
{
  char name[12];
  shortnum age;
} cat;

int main() {
  const unsigned int MAX_MEMBER = 4;
  cat* kittyfield[MAX_MEMBER];

  for (size_t i = 0; i < MAX_MEMBER; i++)
  {
    kittyfield[i] = malloc(sizeof(cat));
    printf("cat name: ");
    scanf("%s", kittyfield[i]->name);
  }

  for (size_t i = 0; i < MAX_MEMBER; i++)
    printf("%s\n", kittyfield[i]->name);

  return 0;
}
```