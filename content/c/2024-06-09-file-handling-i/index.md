---
title: File handling - write
date: 2024-06-09
weight: 31
tags:
  - C
---

Untuk handle (create, write, read) file di C, kamu harus menggunakan typedef `FILE`. `FILE` adalah sebuah typedef file stream.

## Membuka file

Pertama, deklarasikan pointer dengan tipe data `FILE`.

```c
FILE *fptr;
```

Lalu buka file baru dengan `fopen()`. `fopen` akan membuka file baru dengan nama di argument, jika tidak ada maka `fopen` akan membuatnya.

```c
fptr = fopen("players.txt", "w");
```

`"w"` adalah open mode, ada 3 open mode:

|mode|description|
|-|-|
|write (`w`) | menulis ke sebuah file |
|append (`a`) | menulis-timpa ke sebuah file |
|read (`r`) | membaca ke sebuah file |

## Menulis file

Setelah dibuka, sekarang kita sudah bisa menulis apapun kedalam file tersebut, *suppose* kita ingin menulis daftar nama pemain.

Kita menggunakan `fprintf()` untuk menulis sesuatu kedalam file tersebut.

```c
fprintf(fptr, "playername");
```

`fptr` adalah pointer dari file yang sudah kita buka tadi.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
  FILE *fptr;
  fptr = fopen("players.txt", "w");

  int player;
  printf("enter number of players: ");
  scanf("%d", &player);

  for (size_t i = 0; i < player; i++)
  {
    char playername[10];
    printf("player-%d name: ", (i+1));
    scanf("%s", playername);
    fprintf(fptr, "%s\n", playername);
  }
  fclose(fptr);

  return 0;
}
```

Kode diatas akan prompt user nama pemain sesuai jumlah pemain yang ingin dimasukkan. Setelahnya kita harus menutup file menggunakan `fclose()`.