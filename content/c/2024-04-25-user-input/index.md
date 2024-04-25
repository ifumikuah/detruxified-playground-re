---
title: User input
date: 2024-04-25
weight: 9
tags: 
  - C
---

gunakan `scanf` untuk mendapatkan input dari user:

```c
#include <stdio.h>

int main()
{
  int getAge;

  scanf("%d", &getAge);
  printf("%d", getAge);

  return 0;
}
```

Diatas adalah basic dari `scanf`, mengambil input dari user dan menyimpannya kedalam `getAge` melalui memori reference `&`.

## Input lebih dari satu

```c
int main()
{
  int getAge;
  char getClass;

  // Menanyakan (input prompt) umur dan class dari input user
  printf("Insert age and class: ");

  // Mengambil umur dan class dari input user
  scanf("%d %c", &getAge, &getClass);

  printf("\nYour age is %d and assigned to class %c", getAge, getClass);

  return 0;
}
```

## Input string

Pertama, kita harus menentukan dulu besar max yang dapat ditampung dalam sebuah string.

```c
// Max 10 length
char username[10];
```

Kedua, untuk `scanf` tidak perlu lagi menggunakan reference `&` karena bentuknya array.

```c
scanf("%s", username);
```

Contoh lengkap:

```c
#include <stdio.h>

int main()
{
  char username[10];

  printf("Nama: ");
  scanf("%s", username);
  printf("Selamat pagi, %s", username);

  return 0;
}
```

### Input dengan whitespace

Input dengan spasi umum terjadi di string, untuk mengatasi ini gunakan `fget` alih-alih `scanf`.

```c
fgets(username, sizeof(username), stdin);
```

Argumen yang harus dipenuhi adalah:
 1. `username` untuk variable yang ingin kita isi.
 2. `sizeof(username)` untuk mendapatkan max size dari string tersebut.
 3. `stdin` stream, mau di untuk apa variable ini, dalam kasus ini adalah standard input atau `stdin`.

Hasil:

```c
#include <stdio.h>

int main()
{
  char username[20];

  printf("Nama: ");
  fgets(username, sizeof(username), stdin);
  printf("Selamat pagi, %s", username);

  return 0;
}
```