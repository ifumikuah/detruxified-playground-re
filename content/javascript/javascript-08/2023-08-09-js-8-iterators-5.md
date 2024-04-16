+++
title = "Javascript 08: Iterator Method Lainnya"
draft = false
weight = 5
tags = ['javascript']
+++

Semua Iterator Method memerlukan fungsi callback sebagai parameternya. Selain `.forEach()`,`.map()`, dan `.filter()` ada banyak lagi [Method](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) lainnya.

Pastikan memilih method yang tepat untuk memanipulasi array yang dimiliki.

# Method lainnya

Dibawah adalah dua jenis array yang akan digunakan sebagai patokan.

```js
const stringArr = ["Vivian","Lydia","Regolith","Rigel","Vesta","Castello","Prometheus"];
const numArr = [10,21,32,43,54,65,76,87];
```

### .findIndex()

```js
const whichIndex = stringArr.findIndex(function(target){
    return target === "Vesta";
})
```
Output = 4, `.findIndex()` akan mencari nomor index dari data yang diinginkan

### .reduce()

```js
const reducedNum = numArr.reduce(function(acc,curr){
    return acc + curr;
});
```
Output = 388, `.reduce()` akan mengakumulasikan semua jumlah yang ada di sebuah array, method ini efektif untuk array dengan tipe number, tapi juga bisa digunakan untuk string.

```js
const strings = [ 'i', 'l', 'o', 'v', 'e', 'y', 'o', 'u' ];
console.log(strings.reduce((acc,curr) => acc + curr));
```
```plain
iloveyou
```
Contoh barusan menggunakan implicit return arrow function untuk mempersingkat kode.

### .some()

```js
const divisibleByFive = numArr.some((num) => num % 5 === 0);
```
Output `true`, `.some()` memiliki output boolean untuk mengecek apakah salah satu atau lebih dari semua item di array lulus persyaratan yang ada di blok fungsi.

`num % 5 === 0` mengecek apakah angka dapat dibagi habis oleh 5.

### .every()

```js
const byndFour = exampleArr.every((str) => str.length > 4);
```
Output `true`, Sama seperti `.some()`, `.every()` akan langsung output `false` disaat menemukan satu item yang memiliki nilai `false` / tidak sesuai dengan fungsi.

`str.length > 4` mengecek apakah masing-masing kalimat lebih dari 4 huruf.

# Lainnya

Ada beberapa referesi untuk array method.

- [Codecademy](https://www.codecademy.com/resources/docs/javascript/arrays)
- [Mozilla MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [W3Schools](https://www.w3schools.com/jsref/jsref_obj_array.asp)