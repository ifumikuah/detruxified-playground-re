+++
title = "Javascript Regex 01"
draft = false
weight = 1
tags = ['javascript']
+++

Memperkenalkan Regular Expression, atau Regex, sintaks andalan yang mempermudah hidupmu.

## What does it do?

Menyortir karakter, tetapi dengan cara yang lebih keren lagi tentunya.

```js
  // Mencari huruf konsonan yang diapit oleh dua huruf vokal yang sama

  const sentence = "emerging election";
  const regex = /([aeiou])([^aeiou])\1/gi;

  console.log(sentence.match(regex)) // [ 'eme', 'ele' ] ​​​​​at ​​​​​​​​sentence.match(regex)
```

## Cara membuat

Ada dua cara untuk membuat sebuah regex, pertama inisialisasi langsung dengan `/ /` atau menggunakan constructor `RegExp`

Cara *Direct* (`/ /`) adalah cara paling cepat untuk membuat sebuah regex, namun terkadang cara ini cenderung *prone to error*.

Disarankan untuk membuat dengan metode constructor.

```js
const newRegex = new RegExp("")
```

Di metode ini, ada dua cara juga untuk membuat sebuah regex, dengan `" "` seperti diatas atau dengan regex literal `/ /` seperti cara *direct* tadi.

```js
const newRegex = new RegExp(/ /)
//or
const newRegex = new RegExp(" ")
```

Di constructor ini ada dua argument, pertama *pattern* yang ingin kita cari, kedua *flags* untuk opsi terhadap pencarian kita yang akan dibahas nanti.

```js
// Mencari huruf "a" case-insensitive (mengabaikan kapitalisasi) dan global (keseluruhan dari string)
const sentence = "Travos Atroides";
const regex = new RegExp(/a/, "gi");

console.log(sentence.match(regex)) // [ 'a', 'A' ] ​​​​​at ​​​​​​​​sentence.match(regex)
```

## Small Practices

Mencari / menghitung jumlah nama binatang yang cocok dengan array yang diberikan

```js
countAnimals("dog,cat",["dog","cat"]); //=> [1,1]
countAnimals("dog,cat",["dog","cat","pig"]); //=> [1,1,0]
```

Solution:

```js
const countAnimals = (str, arr) => {
  return arr.map((query) => {
    const count = str.match(new RegExp(query, "gi"));
    return !count ? 0 : count.length;
  });
};
```

Link Kata: https://www.codewars.com/kata/5735e39313c205fe39001173/javascript