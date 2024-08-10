---
title: "Polish Notation"
date: 2024-08-10
description: "Prefix notation sebagai ekspresi alternatif dari infix"
tags: [teknologi, c]

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
- name: img04
  src: "img/img04.png"
  title: ""
- name: img05
  src: "img/img05.png"
  title: ""
---

PN atau Polish Notation atau NPN (Normal Polish Notation) atau Prefix adalah notasi dimana operator terletak sebelum kedua operand.

{{< img name=img01 size=small >}}

Tujuan dari ekspresi seperti ini adalah eliminasi bracket yang ada pada infix.

{{< img name=img02 size=small >}}

Evaluasi Operator Prefix adalah dari kiri ke kanan.

Seperti contoh ekspresi diatas, kita memulai dari:

1. `+` sebagai operator.
2. `8` sebagai operand pertama.
3. `*2 + 3 2` sebagai operand kedua.
4. Karena operand kedua masih sub-ekspresi, kita harus evaluasi dengan cara yang sama. Sampai operand kedua adalah sebuah produk akhir.


{{< img name=img03 size=small >}}

Walaupun sudah efisien untuk komputasi, tetap komputer membutuhkan metode yang lebih efisien lagi karena komputasi untuk notasi ini didahului oleh operator daripada operandnya.

Dalam operasi optimalnya, komputer perlu mengetahui kedua operand terlebih dahulu daripada operatornya. Hal ini bisa diatasi dengan cara membacanya dari kanan kekiri.

Atau notasi ini disebut juga dengan *postfix*, sebagaimana operator berada sesudah kedua operand.

## Postfix

{{< img name=img04 size=small >}}

Komputer dapat mengevaluasi ekspresi postfix dengan sangat efisien dengan bantuan stack, komputer bisa mengetahui kapan evaluasi ekspresi bisa dilakukan disaat operator ditemukan.

Untuk operasi `4 6 +` diatas, pertama runtime memasukkan `4` kemudian `6` kedalam stack. Ketika operator dijumpai, operasi dilakukan sekaligus pop kedua operand dari stack tersebut, lalu hasilnya dimasukkan lagi sebagai operand/produk untuk evaluasi selanjutnya.

{{< img name=img05 size=small >}}

Produk akhir seharusnya satu-satunya item didalam stack tersebut.

Untuk implementasinya bisa dilihat di [github](https://github.com/ifumikuah/c-polish-calculator).