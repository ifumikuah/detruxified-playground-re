---
title: Stack vs. heap
date: 2024-05-31
weight: 13
tags:
  - C
---

Saat program berjalan, state  sebuah variable dan fungsi 'disimpan' didalam memori, ada dua jenis memori, yaitu stack dan heap.

Stack adalah memori statik yang ditetapkan oleh compiler saat program utama berjalan. Programmer/user disini tidak memiliki kendali atas seberapa besar memori yang ingin dialokasinya, atau dengan kata lain memori statik.

Heap adalah memori dinamis yang user memiliki kendali penuh terhadapnya, user bebas mau mengalokasikan/resize memori yang akan/sudah dialokasikan, memanfaatkan Heap artinya menggunakan pointer.

Untuk referensi lebih lanjut:

- https://courses.engr.illinois.edu/cs225/fa2022/resources/stack-heap/
- https://www.youtube.com/watch?v=zuegQmMdy8M

