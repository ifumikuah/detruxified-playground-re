---
title: "Linked List V: Reverse List"
date: 2024-08-03
description: "Reverse list"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

Ide reverse list adalah untuk membalikkan urutan list, head menjadi tail dan sebaliknya.

```
*3 -> 5 -> 1 -> 6 -> 8 -> NULL

*8 -> 6 -> 1 -> 5 -> 3 -> NULL
```

Step yang bisa dilakukan untuk menghasilkan hal ini adalah:

1. Menyimpan node selanjutnya dari `curr` sebelum memindahkan `next` dari `curr`.
2. Setelah tersimpan, maka `curr->next` diubah menjadi yang dibelakangnya, atau dengan kata lain `curr->next = prev`.
3. Memajukan `prv` dan `curr` satu langkah kedepan melalui node yang sudah disimpan sebelumnya.

Detailnya bisa dilihat [disini](https://www.figma.com/design/rXwMamgtrPEtN0G5p6HEMk/Reversing-a-linked-list?node-id=0-1&t=w1kfomRuDRarJOLQ-1)

Dalam bentuk blok code akan seperti ini:

```c
while (curr != NULL)
{
  next = curr->next; // tampung alamat sesudah curr;
  curr->next = prev; // pindahkan pointer dari curr->next;
  prev = curr // majukan prev satu langkah kedepan
  curr = next; // majukan curr satu langkah kedepan
}
```

Potongan kode di atas mackbone backbone utama dari operasi ini. Namun setelahnya kamu akan kehilangan `head` karena kita sudah memindahkannya di perulangan sebelunya. Maka `head` perlu di reassign sesudahnya.

Posisi node terakhir yang akan menjadi head ditampung oleh `prev` diakhir perulangan.

```c
head = prev;
```

Wrap it up, full code akan menjadi seperti ini:

```c
/* Reverse list */
void reverse_list()
{
  Node* prev = NULL;
  Node* curr = head;

  while (curr != NULL)
  {
    Node* next = curr->next;

    curr->next = prev;
    prev = curr;
    curr = next;
  }
  
  head = prev;
}
```