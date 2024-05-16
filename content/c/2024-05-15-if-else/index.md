---
title: If else
date: 2024-05-15
weight: 12
tags: 
  - C
---

If else di C.

```c
if (bool_eval) {
  // Execute this block
}
```

```c
if (bool_eval) {
  // Execute this block
} else {
  // Execute this block
}
```

```c
if (bool_eval) {
  // Execute this block
} else if (bool_eval_2) {
  // Execute this block
} else {
  // Execute this block
}
```

Operator seperti biasa:

- `>` atau `>=`
- `<` atau `<=`
- `==` dan `!=`

## Ternary operator

Mempersingkat if else dengan ternary operator.

```c
int a = 24;
int b = 20;
const int biggest = (a > b) ? a : b;
```
Ternary operation:
```c
(a > b) ? a : b
```

Penjelasan: Jika evaluasi `a > b` bernilai `true`, maka return nya `a`, sebaliknya jika `false` maka nilainya `b`.