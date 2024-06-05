---
title: Implementasi array map js di C
date: 2024-06-04
weight: 19
tags:
  - C
---

Implementasi `Array.prototype.map` JavaScript di C.

```c
#include <stdio.h>
#include <stdlib.h>

typedef int (*cb)(int);

int *map(int arr[], int len, cb cbf);
int cbf(int e);

int main() {
  int array[] = {36, 45, 28, 44, 53, 33, 24, 29, 31};
  int arrlen = sizeof(array) / sizeof(array[0]);
  cb ptrf = &cbf;

  int *p_out = map(array, arrlen, ptrf);
  for (size_t i = 0; i < arrlen; i++)
  {
    printf("%d ", p_out[i]);
  }

  free(p_out);
  printf("\n");
  return 0;
}

int *map(int* arr, int len, cb cbf) {
  int* _arr = (int*) calloc(len, sizeof(int));
  for (size_t i = 0; i < len; i++)
  {
    _arr[i] = (*cbf)(arr[i]);
  }
  return _arr;
}

int cbf(int e) {
  return e % 2 == 0 ? e * 2 : e;
}
```