---
title: Two dimensional array pointer
date: 2024-05-28
weight: 12
tags:
  - C

resources:
  - name: img01
    src: "img/img01.png"
    title: ""
  - name: img02
    src: "img/img02.png"
    title: ""
  - name: img03
    src: "img/img03.png"
    title: ""
---

Dibawah adalah diagram dari array dua dimensi.

{{< img name=img01 size=small >}}

Di dua dimensi, `array+n` memiliki behavior sama dengan `&array` di satu dimensi, keduanya **mengarah ke sebuah array of n element**, bukan ke sebuah tipe data seperti `int`, `char` atau yang lainnya.

Mengetahui mengarah kemana sebuah pointer jauh lebih penting daripada alamatnya itu sendiri karena dereference berpatok kepada jenis pointer tersebut untuk mengembalikan valuenya.

```c
#include <stdio.h>

int main() {
  int array[3][2] = {{2, 1}, {4, 3}, {6, 5}};

  printf("%d\n", *(array+1));
  printf("\n");

  return 0;
}
```

Dereference `array+1` akan mengembalikan angka *gibberish*, karena `array+1` menuju ke sebuah array dengan 2 element integer, bukan menuju ke sebuah integer.

Namun, dengan `*(array+1)` kamu sudah mendapatkan alamat element pertama dari array `array+1` tersebut.

{{< img name=img02 size=small >}}

Yang perlu kamu lakukan untuk mendapatkan value dari elemen dua dimensi ini adalah dengan dereference 2 kali `array` ini. Dereference pertama akan memasuki sub-array dan dereference kedua akan memasuki element dari sub-array tersebut.

```c
#include <stdio.h>

int main() {
  int array[3][2] = {{2, 1}, {4, 3}, {6, 5}};

  printf("%d\n", **(array+1));
  printf("\n");

  return 0;
}
```

## Two dimensional address travese

Array dua dimensi adalah sebuah array yang menyimpan array (sub-array), dan di C alamat dari semua element nya saling "berdempetan".

{{< img name=img02 size=small >}}

Maju 1 lompatan dari `*(array+0)` membawa kita ke element kedua dari sub-array pertama atau secara sintaks `*(array+0)+1`.

```c
printf("%p\n", *(array+0)+1);
```

Bagaimana jika `*(array+0)+3`? bukankah sub-array pertama hanya menampung 2 element?.

{{< img name=img03 size=small >}}

`*(array+0)+3` melompati 3x4 bytes (asumsikan tipe data `int`) setelah alamat `*(array+0)`, jadi itu akan overflow ke element dari sub-array sesudahnya.

Alokasi alamat di array dua dimensi akan saling menyambung, ini bisa dibuktikan dengan kode dibawah ini.

```c
#include <stdio.h>

int main() {
  int array[3][2] = {{2, 1}, {4, 3}, {6, 5}};

  for (int i = 0; i < sizeof(array) / sizeof(array[0]); i++)
  {
    for (int j = 0; j < sizeof(array[0]) / sizeof(array[0][0]); j++)
    {
      printf("%d @= %p \n", array[i][j], &array[i][j]);
    }
  }

  printf("\n");

  for (int i = 0; i < (sizeof(array) / sizeof(array[0])) * (sizeof(array[0]) / sizeof(array[0][0])); i++)
  {
    printf("%d @= %p \n", *(*array+i), *array+i);
  }
  return 0;
}

```

Ada dua cara yang digunakan, pertama cara klasik dengan mengakses melalui indeksnya, kedua kita menggunakan pointer arithmetic dari `array`.

## Pointer of two dimensional array

Kita sudah mengetahui bagaimana pointer dan travese alamat bekerja pada array dua dimensi, tapi pertanyaannya bagaimana cara membuat pointer dari array dua dimensi itu sendiri?.

Ingat array dua dimensi menyimpan array, bukan sebuah element satuan seperti integer. Jadi kita harus membuat sebuah pointer yang menuju ke sebuah array.

```c
int (*ptr)[2] = array;
```

`[2]` adalah besar dari sub-array, kita membuat sebuah pointer yang menuju ke sebuah array dengan besar `2` kali element integer.

Menggunakan `ptr` sama dengan bagaimana kita menggunakan `array` pada sebelumnya.
