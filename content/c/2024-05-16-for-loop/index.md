---
title: For loops
date: 2024-05-16
weight: 16
tags: 
  - C
---

Pengulangan `for` loop.

Pengulangan kode untuk waktu yang dibataskan. Untuk pembatasan pengulangan, gunakan `i` atau biasanya indeks sebagai patokan, dan tambahan operator boolean.

Dibawah, akan print nilai `i` selama kriteria `i <= 10` terpenuhi.

```c
for (int i = 0; i <= 10; i++) {
  printf("%d\n", i);
}
```

## Nested loop

```c
int main()
{
  int rows = 5;
  int cols = 8;

  for (int i = 1; i <= rows; i++)
  {
    for (int j = 1; j <= cols; j++)
    {
      printf("%d", j);
    }
    printf("\n");
  }

  return 0;
}
```

Didalam nested loop ini, loop `j` akan dijalan kan sampai selesai, setelah itu loop `i` baru bisa melanjutkan loop selanjutnya dengan menjalankan loop `j` yang sama sampai selesai dan seterusnya, sehingga output seperti ini:
```plain
12345678
12345678
12345678
12345678
12345678
```