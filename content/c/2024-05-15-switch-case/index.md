---
title: Switch case
date: 2024-05-15
weight: 13
tags: 
  - C
---

Memakai `switch` case.

```c
switch (grade) {
  case 'A':
    printf("Letter are A\n");
    break;
  case 'B':
    printf("Letter are B\n");
    break;
  case 'C':
    printf("Letter are C\n");
    break;
  default:
    printf("No matching letter assigned: %c\n", grade);
}
```

Gunakan `break` agar keluar dari blok switch sesudah case yang cocok ditemukan. Case `default` akan dijalankan disaat tidak ada case yang cocok.

`default` tidak perlu `break` karena sudah berada di ujung dari blok switch.