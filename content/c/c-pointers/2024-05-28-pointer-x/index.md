---
title: Pointer in one-dimensional array
date: 2024-05-28
weight: 10
tags:
  - C

resources:
  - name: img01
    src: "img/img01.png"
    title: ""
  - name: img02
    src: "img/img02.png"
    title: ""
  - name: img03
    src: "img/img03.png"
    title: ""
---

Jika sebuah array satu dimensi di deklarasikan.

```c
char array[] = {2, 1, 4, 3, 6, 5};
```

Maka `array` mengarah ke alamat dari element pertama array tersebut.

```c
printf("%p\n", array);
```

Namun, `&array` juga menuju alamat yang sama dengan `array`.

```c
printf("%p\n", array);
printf("%p\n", &array);
```

Alamatnya terlihat sama, namun pointernya berbeda.

- `array` mengarah ke elemen `0` dari array tersebut.
- `&array` mengarah ke array dengan x integer, yaitu keseluruhan array tersebut.

Kamu bisa buktikan dengan menggunakan pointer arithmetic.

```c
printf("%p", &array+1);
printf("%p", array+1);
```

{{< img name=img01 size=small >}}

`&array` melompati alamat 6 x char byte setelah alamat elemen pertama.

## Dereference

Apa yang terjadi jika kamu dereference `&array`.

```c
printf("%d", *&array);
```

Dikaranakan pointer mengarah ke *sebuah array dengan 6 char*, kamu akan mendapatkan value yang tidak ada hubungannya dengan program. Walaupun sebenanya kamu bisa dereference lagi alamat yang barusan di-dereference tadi.

```c
printf("%d", **&array);
```

Kamu mendapatkan hasil value elemen pertama, namun ini sangat tidak berguna dilakukan untuk skenario dunia nyata. Tapi walaupun begitu kamu mengerti bagaimana pointer dan array bekerja.

Bagaimana mengakses value element melalui dereference? Jika berdasarkan diagram diatas tadi, `array` mengarah ke element pertama dari array tersebut, maka `array+1` mengarah ke element selanjutnya dari array, faktanya `array+0` sama dengan `array`.

{{< img name=img02 size=small >}}

Dereference element dengan:

```plain
*(array+1)
```

Perlunya memberi *parentheses* pada `array+1` dikarenakan bagaimana compiler membaca/interpretasi simbol aritmatika.

{{< img name=img03 size=small >}}

## Pointer to an array of x

Kamu ingat kalau `&array` tadi mengembalikan sebuah alamat dari keseluruhan array tersebut.

Kamu bisa menyimpan `&array` tersebut kedalam sebuah variabe pointer lagi.

```c
char array[] = {2, 1, 4, 3, 6, 5};
char (*ptr)[6] = &array;
```

Diatas akan deklarasi sebuah pointer `ptr` mengarah ke sebuah *array of 6 chars*, array yang berisikan 6 elemen char.

```c
printf("%p\t %d\n", &array, *&array);
printf("%p\t %d\n", ptr, *ptr);
```

Keduanya akan menghasilkan value dan alamat yang sama.

Sekali lagi, teknik diatas tidak berguna dilakukan jika array adalah satu dimensi. Namun sangat berguna untuk skenario array multi dimensional nantinya. Sekedar perkenalan semata sebelum mempelajari pointer untuk array multi dimensional.
