---
title: Miniproject
date: 2024-06-03
weight: 17
tags:
  - C
---
Kali ini akan membuat sebuah fungsi yang mereturn sebuah pointer. Jika sebuah array decease menjadi sebuah pointer, apakah kita bisa membuat array sendiri secara dinamis.

Jawabannya bisa menggunakan fungsi yang akan return sebuah pointer. Kita akan membuat fungsi dengan prototype:

```c
int *divBy(int unsorted[], size_t unsortedLen, size_t* sentinel, int modulo);
```

- `int unsorted[]`, array 'mentah' yang akan diproses.
- `size_t unsortedLen`, panjang dari array 'mentah'.
- `size_t* sentinel`, pointer menuju ke value `sentinel` yang nantinya menyimpan panjang dari array baru.
- `int modulo`, modulo untuk mencari element yang memenuhi kriteria.

Disini array baru akan dipenuhi oleh element yang bisa dibagi oleh `modulo` sampai habis.

```c
int main()
{
  int unsorted[] = {12, 32, 55, 10, 36, 75, 44, 45, 10, 50, 79, 80, 100, 64, 65, 128};
  int unsortedLen = sizeof(unsorted) / sizeof(unsorted[0]);

  size_t* sentinel = (size_t *)malloc(sizeof(size_t));
  int* sorted = divBy(unsorted, unsortedLen, sentinel, 16);

  for (size_t i = 0; i < *sentinel; i++)
  {
    printf("%d ", sorted[i]);
  }

  free(sorted);
  printf("\n");
  return 0;
}
```

`sentinel` adalah sebuah pointer, valuenya tersimpan di heap. Kamu bisa juga mempermudahnya dengan menyimpannya di stack dengan tidak memakai `malloc`.

`sorted` akan return sebuah 'array' berisikan angka yang bisa dibagi 16 dari `unsorted`. Dan akan diprint satu-satu sesuai dengan panjang dari `sorted` yang di ambil dari `sentinel`.

## Fungsi sortir

```c
int *divBy(int unsorted[], size_t unsortedLen, size_t* sentinel, int modulo)
{
  *sentinel = 0;
  for (size_t i = 0; i < unsortedLen; i++)
  {
    if (unsorted[i] % modulo == 0)
    {
      (*sentinel)++;
    }
  }

  int* sorted = (int *)calloc(*sentinel, sizeof(int));
  if (sorted == NULL)
  {
    printf("Memory allocation fail!");
    exit(1);
  }

  int j = 0;
  for (size_t i = 0; i < unsortedLen; i++)
  {
    if (unsorted[i] % modulo == 0)
    {
      sorted[j++] = unsorted[i];
    }
  }

  return sorted;
}
```

Simplenya, fungsi diatas pertama akan menghitung penjang dari array baru, dengan menghitung berapa element yang sesuai kriteria.

Lalu memulai alokasi memori sesuai dengan sentinel dikali besar tipe data `int`. Lalu perulangan untuk mengisi value yang sesuai kriteria dimulai di perulangan akhir.