+++
title = "Selector Behavior: querySelectorAll"
draft = false
weight = 3
tags = ['javascript']

[[resources]]
name = "fig1"
src = "fig1.png"
title = ""

[[resources]]
name = "snippet1"
src = "snippet1.png"
title = ""
+++

`querySelectorAll()` *return* element element [(NodeList)](#nodelist) dalam bentuk array.

## NodeList

NodeList merupakan nodes dalam bentuk properti. Semua method DOM seperti `querySelector()`, `querySelectorAll()`, `getElementById()` dan `getElements*` akan *return* setidaknya sebuah [node](https://developer.mozilla.org/en-US/docs/Web/API/Node) jika argument valid.

`querySelectorAll()` dan `getElements*` akan *return* kumpulan node yang disebut dengan [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList).

{{< img name=snippet1 lazy=true size=medium >}}
{{< img name=fig1 lazy=true size=medium >}}

## Fleksibilitas

Dikarenakan *return* NodeList dalam bentuk array, maka kamu bisa men-*treat* hasil `querySelectorAll()` seperti array.

Ada banyak [method array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) yang bisa dicoba, salah satunya `forEach()`.

`querySelectorAll()`, `querySelector()` dan `getElementById()` merupakan method yang umum digunakan.