---
title: Math
date: 2024-04-25
weight: 10
tags: 
  - C
---

Fungsi matematik disediakan jika kamu include header `math` di baris paling atas.

```c
#include <math.h>
```

Dibawah adalah contoh fungsi matematika akar kuadrat.

```c
#include <stdio.h>
#include <math.h>

int main()
{
  float sqroot = sqrt(25);
  printf("%f", sqroot);

  return 0;
}
```

## Fungsi lainnya

- https://www.w3schools.com/c/c_math.php
- https://en.wikipedia.org/wiki/C_mathematical_functions