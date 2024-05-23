---
title: Enums
date: 2024-05-23
weight: 26
tags:
  - C
---

Enums atau enumeration menyimpan beberapa konstant (data yang tidak bisa diubah) dalam satu variable.

```c
enum Level {SANDBOX, EASY, NORMAL, HARD, BRUTAL};
```

Secara default value didalamnya otomatis ter-assign integer dimulai dari 0 jika tidak diberi initial value. Cara memberinya sama seperti assign variable pada umumnya

```c
enum Level {SANDBOX, EASY = 10, NORMAL = 20, HARD = 30, BRUTAL = 99};
```

`SANDBOX` akan tetap bernilai posisinya `0` jika tidak diberikan nilai initial value.

## Mengakses enum

Untuk mengakses enum, kamu harus membuat variabel lagi.

```c
enum Level difficulty = NORMAL;
```

```c
#include <stdio.h>

enum Level {SANDBOX, EASY, NORMAL, HARD, BRUTAL};

int main() {
  enum Level current = NORMAL;

  printf("%d\n", current);
  return 0;
}
```

## Unique behavior

Uniknya, jika kamu mengganti nilai awal dari enum, maka nilai seterusnya akan mengikuti.

```c
#include <stdio.h>

enum Level {SANDBOX = 10, EASY, NORMAL, HARD, BRUTAL};

int main() {
  enum Level current = NORMAL;

  printf("%d\n", current); // 12
  return 0;
}
```