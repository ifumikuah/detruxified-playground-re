---
title: Bitwise operator
date: 2024-05-25
weight: 28
tags:
  - C
---

Bitwise operator adalah operasi yang memanipulasi bit sebuah integer, operasi ini sangat dibutuhkan jika kalian membutuhkan cara efisien untuk menghemat penggunaan memori.

Ada 6 operator bitwise.

## OR

OR `|` menghasilkan 1 jika salah satu atau semua bit adalah 1.

| Operand 1 | Operand 2 | Outcome |
|-|-|-|
| 0 | 0 | 0 |
| 1 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 1 | 1 |

Bagaimana ini berguna?, well, berikan sebuah skenario kamu ingin membuat 3 macam overlapping state dalam 4-bit memory. Apa yang harus dilakukan? bagaimana 3 state tersebut beserta campuran kombinasinya bisa muat dalam 4-bit?.

Satu-satunya cara adalah merepresentasikan ketiga aksi tersebut dalam integer, tetapi integer ini tidak boleh saling tindih tiap statenya.

```plain
EXECUTE = 1
READ = 2
WRITE = 4
```

Ketiga state tersebut direpresentasikan oleh integer yang binernya tidak saling tindih.

```plain
0000 = NULL --> Ini kosong
0001 = 1 EXECUTE
0010 = 2 READ
0100 = 4 WRITE
```

Dengan ini kita bisa membuat kombinasi dari 3 state diatas tanpa ada masalah, kombinasi dua atau lebih state menghasilkan nomor unik yang non-konflik.

Misal kombinasi `READ` dan `EXECUTE` menghasilkan `3` karena `1 + 2 = 3`.

Namun, bagaimana cara kita mengimplementasikan state ini dalam program, yang seharusnya state ini tetap pada aturan mainnya?.

Dengan OR kita bisa menambahkan state yang belum ada sebelumnya, dan tetap membuat state yang sebelumnya ada tidak berubah. Misalkan state user ingin menambahkan state `WRITE` DAN `EXECUTE` pada state yang sebelumnya `NULL`, kemungkinan terjadi 2, antara user memasukkan 4 dan 1 secara sequential, atau memasukkan 5 sebagai cara singkat. Disini kita menggunakan OR agar kedua kemungkinan tersebut menghasilkan outcome yang sama.

```c
#include <stdio.h>

int perm_add(int perm[], int len) {
  int perm_final = 0;
  for (int i = 0; i < len; i++)
  {
    perm_final |= perm[i];
  }
  return perm_final;
}
int main()
{
  int arr[] = {1, 5, 4}; // Insert EXECUTE, EXECUTE+WRITE, , WRITE
  int len = sizeof(arr) / sizeof(arr[0]);

  int user_add = perm_add(arr, len);

  printf("User permission add\t%d\n", user_add); //Hasil EXECUTE+WRITE
  return 0;
}
```

`perm_add()` menggunakan bitwise OR untuk mengambah permission baru, permission tetap menghasilkan kode yang sama walaupun kita memasukkan nilai state yang dimaksud dalam bentuk berbeda.

## XOR

XOR `^` mengembalikan 1 jika salah satu operand adalah 1, jika kedua atau tidak sama sekali operand adalah 1 maka hasilnya 0.

| Operand 1 | Operand 2 | Outcome |
|-|-|-|
| 0 | 0 | 0 |
| 1 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 1 | 0 |

Melihat bahwa `1 ^ 1 = 0`, kita bisa mencancel permission diatas tadi.

```c
#include <stdio.h>

int perm_add(int perm[], int len) {...}

int perm_rm(int current_perm_int, int perm[], int len) {
  for (int i = 0; i < len; i++)
  {
    current_perm_int ^= perm[i];
  }
  return current_perm_int;
}

int main()
{
  int arr_rem[] = {1, 4};
  int len_rem = sizeof(arr_rem) / sizeof(arr_rem[0]);

  int user_remove = perm_rm(7, arr_rem, len_rem);

  printf("User permission remove\t%d\n", user_remove);
  return 0;
}
```

`perm_rm()` butuh tiga argument untuk meremove permission. Pertama, permission id sebelumnya sebagai integer, array id yang ingin di remove, dan panjang array tersebut.

Kode diatas berjalan dengan baik jika dijalankan, `EXECUTE` dan `WRITE` menghilang, meninggalkan `2` sebagai `READ` permission satu-satunya yang ada. Begitu juga jika `{1, 4}` menjadi `{5}`.

Namun, keanehan terjadi jika anda mencoba berulang kali memasukkan id yang sama:
```c
int arr_rem[] = {1, 4, 5, 4};
```
Array diatas hanya berisikan permission untuk `EXECUTE` dan `WRITE` dalam urutan yang berbeda. Jika di tes menggunakan XOR kode diatas tidak efektif untuk menghilangkan permission user.

Cara terbaiknya adalah dengan menggunakan AND `&` Operator.

## AND

AND `&` mengembalikan 1 hanya jika kedua operand adalah 1.

| Operand 1 | Operand 2 | Outcome |
|-|-|-|
| 0 | 0 | 0 |
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 1 | 1 |

Mencoba ulang `perm_rm()` diatas menggunakan AND.

```c
int perm_rm(int current_perm_int, int perm[], int len) {
  for (int i = 0; i < len; i++)
  {
    current_perm_int &= perm[i];
  }
  return current_perm_int;
}
```

Well, hasilnya malah makin tidak jelas, karena kita perlu balikkan/*flip* biner dari tiap `perm[]` element untuk menghasilkan permission sesudah remove nya.

## NOT

Membalikkan biner `~`, ini adalah operasi *unary* yang artinya hanya ada satu operand.

| Operand | Outcome |
|-|-|
| 0 | 1 |
| 1 | 0 |

```plain
0010 = 2
||||
1101 = -3

0011 = 3
||||
1100 = -4
```

Untuk penjelasan mengapa hasilnya negative dan dikurangi 1 angka berada pada, compiler mengasumsikan integer adalah signed integer dalam n-bit dalam artikel ini n adalah 4. Untuk referensi lebih lanjut, silahkan lihat [bit sign](https://en.wikipedia.org/wiki/Sign_bit)

Sekarang mari mencoba lagi `perm_rm()`.

```c
int perm_rm(int current_perm_int, int perm[], int len) {
  for (int i = 0; i < len; i++)
  {
    current_perm_int &= ~perm[i];
  }
  return current_perm_int;
}
```

```c
int arr_rem[] = {1, 4, 5, 4};
int len_rem = sizeof(arr_rem) / sizeof(arr_rem[0]);
int user_remove = perm_rm(7, arr_rem, len_rem);

printf("User permission remove\t%d\n", user_remove);
```

Kode sudah berjalan dengan baik!

## Additionals: shift bit

Operasi bitwise ini menggeser bit kekanan atau kekiri, memerlukan 2 operand yaitu integer dan jumlah geseran.

Dibawah adalah contoh `2 << 2`, menggeser biner dari 2 

```plain
0010 = 2
1000 = 2 << 2 (8) 
```

Simplenya, operasi shifting ini hanya mengkali/membagi 2 integer disetiap geseran. Geser kekiri `<<` akan mengkalikan 2 sebaliknya, geser kekanan `>>` akan membagi dua.