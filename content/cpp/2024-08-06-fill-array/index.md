---
title: Array Fill
date: 2024-08-06
weight: 7
tags:
  - C++
---

`std::fill(array+x, array+y, v)`, mengisi array dari posisi `x` sampai `y` dengan value/nilai `v`.

```cpp
#include <algorithm>

int array[30];

std::fill(&array[0], &array[15], 69);
```

Mengisi setengah dari array dengan value `69`.