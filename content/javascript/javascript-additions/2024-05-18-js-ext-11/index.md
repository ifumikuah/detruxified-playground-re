+++
title = "Everything is an object, but..."
draft = false
weight = 11
tags = ['javascript']
+++

Di javascript ada 2 jenis tipe data:

- Primitives
- Object

## Primitives

Primitives adalah tipedata yang *immutable*, tidak bisa dimanipulasi dan valuenya pada umumnya tertanam langsung di dalam low level.

Tipe data primitive:

- null
- undefined
- string
- number
- boolean
- bigint
- symbol

## Object

Sedangkan object adalah *mutable*, tipe data objek bisa dimanipulasi. Dalam tipe data object terdapat properti dan methods. Properti adalah properti dari object itu seperti length, ukuran bit, address, dll. Methods adalah sesuatu yang bisa dilakukan object ini seperti memanipulasi dirinya sendiri.

Tipe data primitive

- array
- object
- function
- number
- string
- [dan lainnya..](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)

## Kasus untuk number dan string

Bagaimana tipe data seperti number dan string adalah primitive dan object secara bersamaan?, well number primitives js sama seperti primitives biasanya.

Number object dan number primitive adalah 2 hal yang berbeda, hanya saja mereka sama-sama berkaitan dengan angka seperti integer atau float.

```js
const num = new Number(21);
console.log(typeof num);
```

Berbeda dengan

```js
const num = 21;
console.log(typeof num);
```

Sama halnya dengan string, tapi yang menjadi pertanyaan adalah kenapa kita tetap bisa menggunakan method pada string ataupun number primitive walaupun mereka tidak punya method?.

Jawabannya untuk itulah string dan number object dibuat, string primitive akan di-bungkus object otomatis oleh parser js jika kamu menambahkan method di primitive tersebut.

```js
// Keduanya memberikan hasil yang sama tetapi tipe data berbeda
"hello".toUpperCase();
new String("hello").toUpperCase();
```