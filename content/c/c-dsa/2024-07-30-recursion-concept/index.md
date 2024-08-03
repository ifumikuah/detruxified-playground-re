---
title: "Recursion"
date: 2024-07-30
description: "Did you mean recursion?"
tags: [teknologi, c]

resources:
- name: img01
  src: "img/img01.png"
  title: ""
---

Fungsi rekursi adalah suatu fungsi yang memanggil dirinya sendiri. Bentuk dasar dari rekursi adalah:

```c
void diavolo()
{
	diavolo();
}
```

Ketika `diavolo()` dipanggil, `diavolo()` akan memanggil dirinya sendiri dan seterusnya. Fenomena ini disebut juga dengan istilah *Infinite Recursion*.

Kita memerlukan sebuah kondisi dimana fungsi tersebut bisa di-stop sehingga mengembalikan sebuah nilai atau mengeksekusi baris setelahnya.

## Inception Dream Recursion

Dibawah adalah implementasi sederhana dari mimpi dalam film *Inception*. Cobb dan rekannya depat memasuki mimpi target, Fischer secara rekursif sampai sentakan terjadi membuat target terbangun.

```c
void dream(int level)
{
	if (level == 0)
		return;

	dream(level-1);
	printf("entering level %d of target sub-dream\n", level);
}
```

Suatu sentakan akan membuat Fischer terbangun dari mimpinya dan kembali ke kesadaran penuh dunia nyata. Dalam konteks rekursi ini disebut dengan istilah *Base Case*.

```c
if (level == 0)
	return;
```

Di filmnya, Cobb dan timnya dapat memasuki alam mimpi Fischer secara rekursif (mimpi didalam mimpi), disinilah fungsi rekursif dimulai.

```c
dream(level-1);
```

Namun, Cobb dan tim harus segera keluar dari level mimpi paling dalam sebelum kembali terbangun menuju kesadaran (Base Case).

Dalam konteks rekursif ini, fungsi rekursif harus selesai terlebih dahulu sebelum baris dibawahnya dapat dieksekusi.

```c
printf("entering level %d of target sub-dream\n", level);
```

## Counter

Sama seperti *Inception Recursion* diatas, fungsi counter ini mencetak angka dari 1 sampai *n* dengan kode:

```c
void counter(int n)
{
  if (n == 0)
    return;
  
  counter(n-1);
  printf("%d\n", n);
}
```

Secara visual, alur eksekusi sama seperti fungsi *Inception* tadi jika `counter(3)`:

{{< img name=img01 size=large >}}

Perhatikan, tanda panah dari kiri atas. `counter(n)` tidak akan mengeksekusi kode sesudah *recursive call* sampai Base Case terpenuhi.

Di panggilan rekursif ke 4, `counter(0)` memenuhi syarat base case. Panggilan rekursif sebelumnya, yang ke 3 (`counter(1)`) sudah bisa mengeksekusi baris sesudahnya untuk mencetak nilai `n`, dimana `n = 1` dan seterusnya.