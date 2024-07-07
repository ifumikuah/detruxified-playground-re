---
title: Static variable
date: 2024-07-07
weight: 34
tags:
  - C
---

Static variable adalah variable yang persist selama program itu dijalankan. Jadi variable statis nilainya tidak diinisialisasi ulang walaupun dideklarasi didalam sebuah fungsi yang dipanggil berulang kali.

```c
void func() {
	static int n; // sama seperti variable global, nilai default variable static adalah 0
	n++;
	printf("result: %d", n);
}
```

```c
func(); // 1
func(); // 2
func(); // 3
```

*Notice* `n` memiliki nilai yang masih lengket dengan call sebelumnya.