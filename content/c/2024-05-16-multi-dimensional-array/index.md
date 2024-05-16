---
title: Multi dimensional array
date: 2024-05-16
weight: 20
tags: 
  - C
---

Multidimensional adalah sebuah array di yang terdapat beberapa array didalamnya, multi dimensional array bersifat static aslinya, artinya kita harus menentukan panjang "baris" dan "kolom" terlebih dahulu.

Multidimensional array dengan panjang 3 dan panjang 2 di masing-masing sub-array/kolom nya.

```c
int arrs[3][2] = {{1, 2}, {3, 4}, {5, 6}};
```

## Mengakses array multidimensional

Sama seperti array pada normalnya, namun tentukan baris dan kolom seperti menggunakan koordinat cartesius.

```c
int arrs[3][2] = {{1, 2}, {3, 4}, {5, 6}};
int element1 = arrs[0][0] // 1
int element2 = arrs[1][0] // 3
```

## Pengulangan multidimensional array

```c
#include <stdio.h>

int main()
{
  int arrs[3][2] = {{1, 2}, {3, 4}, {5, 6}};
  int row_len = sizeof(arrs) / sizeof(arrs[0]);
  int col_len = sizeof(arrs[0]) / sizeof(arrs[0][0]);

  for (int i = 0; i < row_len; i++)
  {
    for (int j = 0; j < col_len; j++)
    {
      printf("%d ", arrs[i][j]);
    }
    printf("\n");
  }

  return 0;
}
```
