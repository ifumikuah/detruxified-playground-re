---
title: "Recursion: String Reverse"
date: 2024-07-30
description: "Balik sebuah string secara rekursif"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

Fungsi rekursif ini sama cara kerjanya seperti `counter` yang ada di intro [recursion](../2024-07-30-recursion-concept/#counter).

Namun, letak perbedaanya disini `strrev()` mencetak karakter pertama dari setiap panggilan.

```c
void strrev(char* str)
{
  if (*str)
  {
    strrev(str+1);
    printf("%c", *str);
  }
  else
  {
    return;
  }
}
```

Base case adalah `*str == '\0'` atau `str` kosong, `str+1` artinya adalah `str` tapi melompati element pertama / `str[0]` dari string tersebut.

{{< img name=img01 size=medium >}}