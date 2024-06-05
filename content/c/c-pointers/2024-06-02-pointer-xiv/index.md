---
title: Malloc, calloc and free
date: 2024-06-02
weight: 14
tags:
  - C
---
Untuk mengalokasikan memori untuk heap, tiga fungsi digunakan adalah: `malloc()`, `calloc()`, `realloc()`. Untuk membebaskan memori tersebut jika sudah tidak perlu, gunakan `free()`.

```plain
malloc(size_t __size);
```

Keiga fungsi diatas `malloc()`, `calloc()`, `realloc()` akan return sebuah void pointer. Void pointer tersebut adalah alamat awal dari blok memori yang akan digunakan di heap.

```c
malloc(sizeof(int));
```

Diatas akan reserve memori sebesar 4 bytes di heap, namun kita tidak bisa mengakses kedalam memori tersebut dikarenakan `malloc()` return sebuah void pointer. 

Agar bisa diakses, `malloc()` tersebut harus di casting ke tipe data yang ingin digunakan.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
  int* x = (int*) malloc(sizeof(int));
  return 0;
}
```

Lalu kita bisa mengakses didalam alamat memorinya.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
  int* x = (int*) malloc(sizeof(int));
  *x = 49;

  printf("%d \n", *x);
  return 0;
}
```

Namun ketika `malloc()`  belum diberikan initial value, compiler akan memberikan value *gibberish* didalam memori tersebut.

```c
int* x = (int*) malloc(sizeof(int));

printf("%d \n", *x);
```

`calloc()` akan memberikan nilai default nol (binary zero) saat dideklarasikan.

```plain
calloc(size_t __nmem, size_t __size)
```

Argument harus diisi adalah secara berurut: `__nmem` kali dari `__size` yang ingin dialokasikan dan yang kedua: besar (byte) dari memori yang ingin dialokasikan.

Misal jika kamu ingin mengalokasikan sebesar 5 kali dari sebuah `int`, sintaksnya:

```c
int* x = (int*) calloc(5, sizeof(int));
```

Uniknya, memori reserved di heap ini memiliki sifat yang mirip seperti array karena sebuah array *deceased* menjadi sebuah pointer.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
  int* x = (int*) calloc(3, sizeof(int));
  *x = 10; // same as x[0] || *(x+0)
  x[1] = 15; // same as *(x+1)
  *(x+2) = 20; // same as x[2]

  for (int i = 0; i < 3; i++)
  {
    printf("%d \n", x[i]);
  }
  
  return 0;
}
```

Demonstrasi diatas memiliki 3 cara yang berbeda untuk mendefinisikan masing masing value dari blok memori yang direserve.

## Free

Ketika memori di heap tadi tidak diperlukan, bersihkan menggunakan `free()`. Memori teresbut akan dibebaskan untuk dipakai alokasi baru yang akan mendatang jika ada.

```plain
free(*ptr)
```

Argument `free()` hanyalah sebuah pointer.

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
  int* x = (int*) calloc(3, sizeof(int));
  *x = 10;
  x[1] = 15;
  *(x+2) = 20;

  for (int i = 0; i < 3; i++)
  {
    printf("%d \n", x[i]);
  }

  free(x);
  return 0;
}
```