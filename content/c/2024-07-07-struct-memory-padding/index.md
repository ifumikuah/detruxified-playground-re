---
title: Struct memory padding
date: 2024-07-07
weight: 39
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
- name: img04
  src: "img/img04.png"
  title: ""
---

Struct memory padding terjadi karena cycle processor yang hanya dapat membaca data sebesar 1 word tiap satu cycle.

**1 word = 1 cycle**

Ukuran per word ditentukan oleh arsitektur komputernya, 4 bytes untuk 32-bit dan 8 bytes untuk 64-bit.

Mari membuat sebuah struct yang terdiri atas `char`, `char` dan `int` secara berurutan, membuat total size struct tersebut adalah 1+1+4 bytes.

```c
typedef struct S {
	char x;
	char y;
	int z;
} struc;
```

Maka yang seperti biasa orang awam pikirkan, distribusi lokasi seharusnya akan sama halnya seperti array.

{{< img name=img01 size=large >}}

Namun struct tidak seperti itu. Processor membaca data dalam per-cycle yang ukurannya telah ditetapkan. Dalam sistem 32-bit satu cycle adalah 4 bytes, jadi artinya processor dapat membaca 4 bytes data dalam satu siklus read nya.

{{< img name=img02 size=large >}}

Gambaran diatas menunjukan bahwa terdapat sisa 2 byte dalam membaca sebuah struct tadi. `int` membutuhkan 2 kali cycle untuk dibaca oleh processor, tentunya ini merupakan pemborosan komputasi semenjak CPU memakan resource banyak setiap kali mengakses `int` tersebut.

Solusi yang ditawarkan oleh compiler (dalam hal ini C) adalah dengan memberi sebuah jarang / *padding* pada memori. Dengan ini kebalikannya terjadi, mengorbankan memori dan menyelamatkan CPU.

{{< img name=img03 size=large >}}

## Urutan member ditukar

Apa yang terjadi jika urutan member secara urut adalah `char`, `int`, `char` ?. Dikarenakan C adalah bahasa yang procedural (eksekusi dari atas ke bawah), maka padding compiler mengikuti urutan deklarasi member ini.

```c
typedef struct S {
	char x;
	int z;
	char y;
} struc;
```

{{< img name=img04 size=large >}}

Terjadi pemborosan memori lebih jauh sehingga struct memakan memori sampai 12 bytes.