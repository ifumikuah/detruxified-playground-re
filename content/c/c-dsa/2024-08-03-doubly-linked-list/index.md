---
title: "Doubly Linked List"
date: 2024-08-03
description: "Doubly linked list"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

{{< img name=img01 size=small >}}

Doubly linked list adalah varian dari linked list, dimana node nya memiliki `prev` pointer, mengarah ke node sebelumnya. Ini meng-improve fleksibilitas dari list disaat yang sama mengorbankan size dari data yang digunakan.

```c
struct Node {
  int data; // 4 bytes
  struct Node* prev; // 8 bytes
  struct Node* next; // 8 bytes
}
```

Memakan size sebesar 20 bytes per nodenya.

Namun, berbeda dengan singly linked list, doubly linked list mempermudah operasi list dikarenakan akses ke node sebelumnya.

## Pembuatan node

Sama seperti singly linked list, tambahannya kita perlu memberikan nilai untuk `node->prev`.

Menambah sebagai head:

```c
void add_head(int data)
{
  Node* new = malloc(sizeof(Node));
  new->data = data;

  if (root == NULL)
    new->next = NULL;
  else
  {
    root->prev = new;
    new->next = root;
  }

  new->prev = NULL;
  root = new;
}
```

Sebagai tail:

```c
void add_tail(int data)
{
  Node* prev = NULL;
  Node* curr = root;

  while (curr != NULL)
  {
    prev = curr;
    curr = curr->next;
  }

  if (prev == NULL)
    add_head(data);
  else
  {
    curr = malloc(sizeof(Node));
    curr->data = data;
    curr->prev = prev;
    curr->next = NULL;
    prev->next = curr;
  }
}
```

## Additionals

Menghapus node di posisi x.

```c
void free_node(int pos)
{
  if (pos < 1)
    return;
  
  Node* curr = root;
  while (--pos)
  {
    if (curr->next == NULL)
      break;
    
    curr = curr->next;
  }
  
  if (curr == root)
  {
    curr->next->prev = curr->prev;
    root = curr->next;
    free(curr);
    return;
  }
  else if (curr->next == NULL)
  {
    curr->prev->next = curr->next;
    free(curr);
    return;
  }
  else
  {
    curr->prev->next = curr->next;
    curr->next->prev = curr->prev;
    free(curr);
  }
}
```

Untuk menambah di posisi x, seharusnya memiliki mekanisme yang serupa.