---
title: Array pointer case
date: 2024-05-28
weight: 11
tags:
  - C

resources:
  - name: img01
    src: "img/img01.png"
    title: ""
---

Sebuah kasus dimana variable char `x` ditambahkan kedalam kode.

```c
#include <stdio.h>

int main() {
  char x = 79;
  char array[] = {2, 1, 4, 3, 6, 5};
  char (*ptr)[6] = &array;

  printf("ptr+1\t  = %p \n", ptr+1);
  printf("array+6\t  = %p \n", array+6);
  printf("&x\t  = %p \n", &x);

  return 0;
}
```

Berdasarkan diagram di artikel sebelumnya. `&array+1` atau dalam hal ini `ptr+1` menghasilkan alamat sesudah array tersebut, yakni alamatnya `x` (compilermu bisa saja mengalokasikan pada alamat sebelum array).

{{< img name=img01 size=small >}}

Bagaimana jika kita dereference untuk reveal nilai masing masing address.

```c
#include <stdio.h>

int main() {
  char x = 79;
  char array[] = {2, 1, 4, 3, 6, 5};
  char (*ptr)[6] = &array;

  printf("ptr+1\t  = %d \n", *(ptr+1));
  printf("array+6\t  = %d \n", *(array+6));
  printf("&x\t  = %d \n", *(&x));

  return 0;
}
```

Lihat bagaimana `*(&array+1)` atau `*(ptr+1)` menghasilkan value *gibberish*. Ini dikarenakan tipe pointernya adalah **pointer yang menuju ke sebuah array dengan 6 char**.

`*(array+6)` dan `*(&x)` menghasilkan value sebenarnya dikarenakan tipe pointernya adalah **pointer yang menuju ke sebuah tipe data char**.
