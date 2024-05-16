---
title: While loops
date: 2024-05-16
weight: 17
tags: 
  - C
---

`while` loop mengeksekusi blok kode dalam waktu yang tidak ditentukan.

```c
while (boolean_true) {
  // Run this block
}
```

Selama evaluasi boolean yang ada pada `while` bernilai `true`, maka blok akan terus berjalan, membuka kemungkinan infinity loop.

Cara terbaik adalah dengan memberi sebuah batasan didalam blok tersebut.

```c
int main () {
  int i = 100;
  while (i > 0) {
    printf("Turn: %d\n", i);
    i -= 10;
  }

  return 0;
}
```

Diatas akan mengulangi blok `while` selama nilai `i` lebih besar daripada 0, namun dikarenakan angka `i` yang terus menurun seiring perulangan, eksekusi `while` akan berhenti jika `i > 0` bernilai `false`.

Dalam `while` loop, kondisi tidak sebatas angka seperti halnya `for` loop, bisa segala hal yang tentunya return sebuah nilai boolean. Disitulah kelebihan `while` loop daripada `for` loop.

## Do while loop

Variasi lain dari `while` loop, do while akan mengeksekusi setidaknya sekali blok perulangan walaupun tidak memenuhi kriteria `while`.

```c
int main () {
  int i = -10;
  do {
    printf("Turn: %d\n", i);
    i -= 10;
  } while (i > 0);

  return 0;
}
```
```plain
Turn: -10
```
