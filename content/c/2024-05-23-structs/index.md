---
title: Structs
date: 2024-05-23
weight: 23
tags:
  - C
---

Structures atau dikenal *struct* adalah cara untuk mengelompokan variabel dengan berbagai tipe data, variable yang ada di structure disebut juga *member*. Struct mirip seperti class yang dimiliki oleh high-level language

```c
struct Car { // Deklarasi struct
  char class; // Member
  int year;  // Member
  double speed; // Member
};
```

## Membuat struct variable

Untuk menggunakan struct yang dibuat diatas tadi, mirip seperti constructor class.

```c
struct Car car1 = {'C', 1970, 15.45};
```

Structure car1 sudah terbuat, yang merupakan anggota dari `Car`.

## Mengakses struct

Kita akan mengakses dan manipulasi value dari struct `car1`.

```c
car1.year = 1980;
car1.class = 'S';
car1.speed = 20.05;
```

Mencetak struct.

```c
printf("Year: %d\nClass: %c\nSpeed: %.2lf\n", car1.year, car1.class, car1.speed);
```

## String di struct

Menggunakan string di struct artinya kita harus utilize `string.h`, karena string merupakan `char` yang ditumpuk dalam sebuah array.

```c
#include <stdio.h>
#include <string.h>

struct Person
{
  char name[10];
  int age;
};

int main() {
  struct Person person1 = {"Robert", 28};

  person1.age = 25;
  strcpy(person1.name, "Mark");

  printf("Name: %s\nAge: %d\n", person1.name, person1.age);
  return 0;
}
```

Kita menggunakan `strcpy()` untuk assign `"Mark"` ke `person1.name`.