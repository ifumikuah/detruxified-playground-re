---
title: "Infix expression"
date: 2024-08-10
description: "Infix notation sebagai ekspresi yang sering dipakai sehari-hari"
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
---

Infix adalah notasi aritmetika yang sering digunakan sehari-hari, notasi klasik dengan operator diatara dua operand.

{{< img name=img01 size=small >}}

Namun, infix tidak efisien digunakan komputer walaupun manusia memahaminya dengan mudah. Komputer harus mencari urutan operasi (PEMDAS) berdasarkan tingkatan operator, bolak-balik sehingga memakan sumber daya.

{{< img name=img02 size=small >}}

Ini tidak efisien sebagaimana komputer harus mengulagi iterasi setiap operator ditemukan.

## Parenthesis

Parenthesis juga salah satu alasan mengapa ekspresi infix ini tidak ramah komputer, komputer harus mencari dan parsing tanda kurung terlebih dahulu sebelum sub-ekspresi bisa di evaluasi.

{{< img name=img03 size=small >}}

Dengan ekspresi diatas, komputer harus:

1. Iterasi operator berdasarkan tingkatan.
2. Mencari kurung yang paling terdalam jika ada.
3. Jika ada, maka parsing ekspresi yang ada di dalam kurung tersebut.
4. Ulangi.

Urutan operasi diatas akan membebani komputer sebagaimana komputer harus maju-mundur untuk mencari sesuai urutan.