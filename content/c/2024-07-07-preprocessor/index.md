---
title: Preprocessor
date: 2024-07-07
weight: 36
tags:
  - C
---

Sebelum code diubah ke biner oleh compiler, ada step ditengah-tengahnya, yaitu preprocessor.

[Preprocessor](https://en.wikipedia.org/wiki/C_preprocessor) adalah header yang didefine di awal-awal code, dengan awalan `#`.

```
#include <stdio.h> // ini adalah preprocessor
#include "mylib.h" // ini juga preprocessor
```

![[Pasted image 20240701143253.png]]

*Directive* preprocessor tidak hanya `#include`, ada juga yang [lain](https://www.geeksforgeeks.org/cc-preprocessors/) seperti `#define`, `#pragma`, `#undef` dan [lain-lainnya](https://www.petanikode.com/c-macro/)

## What actually preprocessor's do

Ketika kamu define `#include` diawal code, maka preprocessor akan "mencopy" semua prototype dari fungsi yang ada.

Misal:

```
#include <stdio.h>
```

Akan menginstruksikan compiler kalau semua fungsi yang ada di `stdio.h` dibutuhkan, maka compiler akan "mengcopy" semua prototype yang tertulis oleh `stdio.h` termasuk `printf()` untuk digunakan fungsi main atau sejenis dalam file program tersebut.