+++
title = "Javascript Intermediate 01: Inheritance Introduction"
draft = false
weight = 3
tags = ['javascript']

[[resources]]
name = "inheritance"
src = "inheritance-1.png"
title = "Parent class inherit"
+++

{{< img name=inheritance size=medium >}}

Dikarenakan Kucing dan Anjing sama-sama binatang, mereka pasti memiliki beberapa kesamaan namun juga memiliki perbedaan.

Properti yang sama seperti nama dan sifat akan di inherited/diturunkan dari parent class `Animal`. Properti berbeda seperti `usesLitter` yang hanya ada pada kucing, akan hanya bisa diakses oleh sub-class kucing.

Dengan konsep inheritance, kamu bisa membuat Parent class (superclass) dengan properti yang dapat diakses oleh Child classes (subclass). Ini membuat kode lebih efisien dan lebih mudah dibaca.