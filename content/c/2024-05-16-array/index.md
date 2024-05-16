---
title: Array
date: 2024-05-16
weight: 19
tags: 
  - C
---

Array di C hanya bisa menyimpan datatypes yang sama.

```c
// Array dengan isi integer
int integers[] = {11, 22, 33, 6};

// Array dengan isi double
double doubles[] = {1.85, 80.80, 3.14};

// Array dengan isi char
char chars[] = "patrick";
```

## Mengakses

Untuk akses elemen array gunakan index dari 0.

```c
// Print elemen pertama dari array integers
int integers[] = {11, 22, 33, 6};
printf("Number: %d\n", integers[0]);
```

## Manipulasi

Manipulasi element didalam array.

```c
// Ubah index ketiga (terakhir) menjadi 44
int integers[] = {11, 22, 33, 6};
integers[3] = 44;
printf("Number: %d\n", integers[4]);
```

## Panjang array

C tidak mempunyai fungsi built-in untuk menentukan panjang array, salah satunya cara mudah untuk mengakali ini adalah dengan mencari ukuran array tersebut dibagi ukuran salah satu element. 

Semenjak array di C harus memiliki satu tipe data yang sama, ini artinya setiap element memiliki ukuran yang sama satu sama lain.

```c
int integers[] = {11, 22, 33, 6};
int arrlength = sizeof(integers) / sizeof(integers[0]);

printf("Length of array: %d\n", arrlength);
```

Contoh dibawah akan print akar 2 dari setiap element didalam array:
```c
#include <stdio.h>
#include <math.h>

int main()
{
  int integers[] = {2, 5, 12, 15};
  int arrlength = sizeof(integers) / sizeof(integers[0]);

  for (int i = 0; i < arrlength; i++)
  {
    printf("%.0f\n", pow(integers[i], 2));
  }
  
  return 0;
}
```