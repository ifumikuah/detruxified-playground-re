---
title: "Stack data structures"
date: 2024-08-03
description: "Stack"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

**Stack** adalah data structure linear yang bekerja sesuai aturan LIFO (Last in first out). Dimana element pada tipe data ini seperti tumpukan lapisan burger.

Bayangkan sebuah burger yang terdiri atas:

```
Roti
Tomat
Selada
Keju
Patty
Roti
```

Untuk mengambil selada, pastinya roti dan tomat harus diangkat terlebih dahulu secara berurut. Hal yang sama juga terjadi jika ingin mengambil patty nya.

Atau contoh sempurna nya adalah permainan logika [Tower of Hanoi](https://en.wikipedia.org/wiki/Tower_of_Hanoi).

## Operasi pada stack

Operasi pada stack umumnya:

1. Push
2. Pop
3. Peek
4. IsEmpty
5. Size

## Implementasi pada array

Stack bisa diimplementasikan pada array dengan catatan:

1. Array merupakan struktur static, artinya data overflow bisa terjadi. Untuk mencegah overflow terjadi, array tersebut harus di increase lagi sizenya dengan menduplikat data sebelumnya dimana hal ini mengorbankan *time complexity* sebesar **O(n)**.

2. Array adalah struktur yang paling mudah untuk diimplementasikan dengan tingkat kerumitan paling rendah dibandingkan Linked List.

Yang dibutuhkan untuk implementasi stack di array adalah:

1. Sebuah array.
2. Sebuah variable posisi element terakhir pada saat ini.

Keduanya akan di declare di global.

```c

#define MAXLEN 100

int array[MAXLEN];
int last;
```

Lalu, pada `main()` define `last` menjadi `-1`, yang artinya array kosong.

### Push

Push adalah routine untuk menambahkan ke tumpukan.

```c
void push(int data)
{
  last++;
  array[last] = data;
}
```

Mengikuti aturan `last`, maka element akan ditambahkan ke array index ke `last`.

### Pop

Pop adalah routine untuk menarik / membebaskan element yang terakhir kali ada di tumpukan.

```c
void pop()
{
  if (last == -1) return;
  last--;
}
```

Kita hanya perlu mengurangi `last`.

Tapi mengapa begitu?, karena nantinya data yang lama akan otomatis ditimpa oleh data yang baru sebagaimana kita hanya perduli dengan data yang ada pada `last` dan dibawahnya.

Sebagai tambahan, kita juga harus membuat sebuah case prevention jika array kosong. Jika kosong atau `last == -1` maka jangan lakukan apapun.

### Peek

Peek adalah routine yang paling mudah, yang dilakukannya hanya mengekstrak nilai terakhir.

```c
int peek()
{
  return array[last];
}
```

### IsEmpty

Mengecek apakah array kosong atau tidak.

```c
bool isEmpty()
{
  if (last == -1)
    return true;
  else
    return false;
}
```

### Size

Mengembalikan besar dari stack.

```c
int size()
{
  return last+1;
}
```