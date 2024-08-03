---
title: "Recursion: Factorial"
date: 2024-07-30
description: "Menemukan factorial dengan fungsi recursive"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

Kamu pasti tidak percaya jika kita bisa membuat fungsi paling singkat di C untuk mencari faktorial, umumnya orang menggunakan loop untuk mencarinya.

```c
unsigned long factorial(int n)
{
  int sum = 1;
  for (int i = sum; i <= n; i++)
    sum *= i;

  return sum;
}
```

Namun, dengan rekursi kita bisa membuat definisi fungsi tersebut dalam satu baris.

```c
unsigned long factorial(int n)
{
  return n > 1 ? n * factorial(n-1) : 1;
}
```

Dengan visualisasi:

{{< img name=img01 size=small >}}