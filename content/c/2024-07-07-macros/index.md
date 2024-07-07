---
title: Macros
date: 2024-07-07
weight: 37
tags:
  - C
---

Macros adalah bagian dari preprocessor. Ketika compiler menjumpai sebuah macro, maka definisi dari macro akan digantikan oleh nama macro tersebut.

```c
#define PI 3.141592
```

Maka nilai `3.141592` digantikan oleh textual `PI`.

```c
#define PI 3.141592

int main() {
	double r = 4.65;
	double circ = PI*r*r;
	return 0;
}
```

## Function macro

Macro bisa diberi argument layaknya fungsi.

```c
#include <stdio.h>
#define add(x, y) (x + y)

int main() {
	int addition = add(2, 2);

	printf("sum is: %d", addition);
	return 0;
}
```

Akan tetapi, macro seperti ini tidak reliable untuk skenario kompleks, karena fungsi memiliki data type validation ketimbang macro yang tidak memilikinya.

## Macro conditionals

Kamu bisa mengatur bagaimana preprocessor membaca macro dengan menambahkan kondisi dengan `#ifdef`.

`#ifdef` artinya jika `x` didefinisikan, maka macro yang didalamnya akan digunakan.

```c
#include <stdio.h>
#define OS_UNIX

#ifdef OS_UNIX
  #define BUFF 200
#endif

#ifdef OS_MS
  #define BUFF 450
#endif

int main() {
  printf("buffersize: %d\n", BUFF);
  return 0;
}
```

Nilai `BUFF` akan menjadi `200` dikarenakan kita mendefinisikan macro `OS_UNIX`.