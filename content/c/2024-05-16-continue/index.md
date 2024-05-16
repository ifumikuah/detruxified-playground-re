---
title: Break & continue
date: 2024-05-16
weight: 18
tags: 
  - C
---

## Break

`break` sama halnya seperti di switch case, akan segera keluar dari blok saat ini dijalankan disaat `break` ditemukan.

```c
for (int i = 1; i >= 20; i++ ) {
  // Keluar dari perulangan jika ketemu 13
  if (i == 13) {
    break;
  }
}
```

## Continue

`continue` akan melompati perulangan alih-alih keluar dari perulangan tersebut;

```c
for (int i = 1; i >= 20; i++ ) {
  // Melompati perulangan jika ketemu 13
  if (i == 13) {
    continue;
  }
}
```

Akan mencetak hanya angka ganjil.

```c
  int threshold = 20;

  for (int i = 1; i <= threshold; i++)
  {
    // Lompati perulangan jika i = genap
    if (i % 2 == 0)
    {
      continue;
    }
    
    printf("%d\n", i);
  }
```