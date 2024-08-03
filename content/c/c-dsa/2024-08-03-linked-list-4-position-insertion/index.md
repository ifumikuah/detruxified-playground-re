---
title: "Linked List IV: Position Insertion"
date: 2024-08-03
description: "Insert node linked list di posisi tertentu"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
- name: img02
  src: "img/img02.png"
  title: ""
---

Ide position insertion pada linked list adalah dengan mengambil informasi mengenai element sebelum posisi yang ingin dimasukan.

{{< img name=img01 size=small >}}

Kita ingin insert node baru di posisi ke tiga, tempat dimana saat ini `5` berada. Maka kita harus menggeser `5` ke kanan.

Kita menggeser `5` kekanan melalui element sebelumnya, yaitu `2`.

Stepnya seperti ini:

{{< img name=img02 size=small >}}

## Berpatok pada node sebelum posisi

Jika ingin mengambil posisi 3, maka kita harus berpatok pada node sebelumnya. Pertama kita harus menyimpan element sebelumnya dan juga sesudahnya di variable pointer sementara.

```c
Node* prev = NULL;
Node* curr = root;
``` 

Nantinya, kita traverse `curr` sampai posisi yang diinginkan, sementara `prev` diisi oleh node sebelumnya. Jika `curr` adalah `root` atau tidak ada perpindahan posisi, maka `prev` adalah `NULL` yang akan menjadi case khusus nantinya.

```c
while (--pos)
{
  prev = curr;
  curr = curr->next;
}
```

Kita akan terus traverse sampai `pos` adalah `0`. Maka evaluasi menjadi `false` dan while-loop berhenti.

Definisi fungsi akan menjadi seperti ini:

```c
void pos_insert(int pos, int data)
{
  Node* prev = NULL;
  Node* curr = root;

  while(--pos)
  {
    prev = curr;
    curr = curr->next;
  }
}
```

Kita juga harus memberi keamanan tambahan untuk menghindari argument yang tidak diingikan.

```c
void pos_insert(int pos, int data)
{
  if (pos < 1) return; // Abaikan call jika pos dibawah 1

  Node* prev = NULL;
  Node* curr = root;

  while(--pos)
  {
    prev = curr;
    curr = curr->next;

    if (curr->next == NULL) break; // Langsung keluar perulangan jika sudah sampai node terakhir
  }
}
```

## Insert node baru

Memasukkan element baru semudah menambah di tail atau head, hanya saja ada adjusting tambahan seperti yang ditunjukkan diagram.

```c
void pos_insert(int pos, int data)
{
  if (pos < 1) return; // Abaikan call jika pos dibawah 1

  Node* prev = NULL;
  Node* curr = root;

  while(--pos)
  {
    prev = curr;
    curr = curr->next;

    if (curr == NULL) break; // Langsung keluar perulangan jika sudah sampai node terakhir
  }
}
```

Buat node baru dengan `malloc`.

```c
Node* new = malloc(sizeof(Node));
new->data = data;
```

Lalu, kita perlu adjusting pointer jika posisi berada tidak sebagai head.

```c
new->next = curr;
prev->next = new;
```

Jika posisi sebagai head, maka kita ubah node baru tersebut menjadi head.

```c
new->next = curr;
root = new;
```

Wrapping up, code fullnya akan menjadi seperti ini:

```c
void pos_insert(int pos, int data)
{
  if (pos < 1) return; // Abaikan call jika pos dibawah 1

  Node* prev = NULL;
  Node* curr = root;

  while(--pos)
  {
    prev = curr;
    curr = curr->next;

    if (curr == NULL) break; // Langsung keluar perulangan jika sudah sampai node terakhir
  }

  Node* new = malloc(sizeof(Node));
  new->data = data;

  if (curr != root)
  {
    new->next = curr;
    prev->next = new;
  }
  else
  {
    new->next = curr;
    root = new;
  }
}
```