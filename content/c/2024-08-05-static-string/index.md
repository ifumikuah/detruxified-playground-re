---
title: Static String
date: 2024-08-05
weight: 41
tags:
  - C

resources:
- name: img01
  src: "img/img01.png"
  title: ""
- name: img02
  src: "img/img02.png"
  title: ""
---

Static string adalah dekralasi dan assigning string secara langsung di C, tanpa malloc.

```c
char* cat = "Gli";
```

Diatas adalah static string, nilai dari karakter yang ada di string tersebut disimpan langsung didalam memori yang bersifat *read-only*.

Static string berbeda dengan string yang dideklarasi dengan array:
```c
char cat[] = "Gli";
```

Walaupun memiliki schema yang sama, array berbeda dengan pointer. Sebuah array `cat` menampung alamat dari element pertamanya, sama halnya seperti pointer char `cat`. Namun sebuah array bukanlah pointer.

{{< img name=img02 size=small >}}
{{< img name=img01 size=small >}}

Tampaknya sama, namun berbeda. Ini bisa dibuktikan dengan `sizeof`, dimana array menampung value char tersebut sebanyak `length("Gli")*sizeof(char)` besarnya.

```c
char cat[] = "Gli";
printf("%d", sizeof(cat)); // 4 bytes (with null terminator)
```

Namun, pointer menampung sebesar 8 bytes mau berapapun panjang stringnya, sebagaimana pointer seharusnya memiliki besar 8 bytes (64bit).

```c
char* cat = "Gli";
printf("%d", sizeof(cat)); // 8 bytes
```

## Array of static string

Kamu bisa membuat array of strings, lebih tepatnya static string.

```c
char* cats[] = {"Gli", "Bob", "Palmerstone", "Larry", "Oskar"};
```

Array of static strings ini menyimpan pointer to char kedalam array lebih tepatnya. Disini ada 5 item (pointer to char), maka array ini memiliki besar `5*8` bytes.

Uniknya kamu bisa menambah `NULL` kedalamnya, karena secara teknis `NULL` adalah pointer juga.

```c
char* cats[] = {"Gli", "Bob", "Palmerstone", "Larry", "Oskar", NULL};
```

Ini berguna jika ingin menemukan akhir dari array of pointer tersebut.