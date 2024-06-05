---
title: Command argument
date: 2024-05-25
weight: 31
tags:
  - C
---

Passing argumen command line di C.

```c
int main(int argc, char* argv[]) {
  return 0;
}
```

`int argc` membaca panjang argumen yang dimasukkan, argumen yang dimasukkan minimal 1.

Program yang dijalan kan adalah argumen yang pertama, atau `argv[0]`.

Jika prompt user adalah:
```c
> run_progs hello world
```

Maka `argc` adalah `3` dan:
```plain
argv[0] adalah run_progs
argv[1] adalah hello
argv[2] adalah world
```
