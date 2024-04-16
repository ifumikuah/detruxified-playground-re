+++
title = "Javascript 07: Whale Talk"
draft = false
weight = 8
tags = ['javascript']
+++

Program *Whale Talk*/ bahasa paus, dengan menerjemahkan input bahasa manusia ke bahasa paus.

### Peraturan

tahapan menerjemahkan bahasa manusia ke bahasa paus :
1. Tidak ada konsonan, hanya ada vokal.
2. huruf *u* dan *e* dibaca panjang.

### Code

```js
const input = "turpentine and turtles";
const vowels = ["a","i","u","e","o"];

let resultArray = [];

for (let i = 0; input.length > i; i++) {
    if (input[i] === 'e') {
        resultArray.push(input[i]);
    }

    if (input[i] === 'u') {
        resultArray.push(input[i]);
    }

    for (let j = 0; vowels.length > j; j++) {
        if (vowels[j] === input[i]) {
            resultArray.push(vowels[j]);
        }
    }
}

const resultString = resultArray.join('');

console.log(resultString.toUpperCase());
```
```plain
UUEEIEEAUUEE
```
# Penjelasan

### Variabel input, vowels dan resultArray

`input` sebagai input bahasa manusia.

`vowels` berisi array huruf vokal yang digunakan bahasa paus.

`resultArray` menyimpan hasil terjemahan bahasa manusia ke bahasa paus.

### Pemanjangan vokal 'e' dan 'u'

```js
for (let i = 0; input.length > i; i++) {

    if (input[i] === 'e') {
        resultArray.push(input[i]);
    }

}
```
Di dalam blok loop utama terdapat dua *if* untuk `input[i] = 'e'`, yang akan memasukkan huruf `e` sekali lagi disaat loop utama menemukan huruf `e`.

### Penerjemahan ke bahasa paus

```js
for (let j = 0; vowels.length > j; j++) {
        if (vowels[j] === input[i]) {
            resultArray.push(vowels[j]);
        }
    }
```
Looping terakhir merupakan dimana bahasa manusia diterjemahkan. loop diatas akan mencetak setiap kali ada huruf di `input` yang sama dengan `vowel` (mencari huruf vokal), lalu hasilnya akan dimasukkan ke `resultArray`.

### Merapikan susunan

```js
const resultString = resultArray.join('');
console.log(resultString.toUpperCase());
```

Untuk merapikan output, semua item array akan dihapuskan penghubungnya dengan `join()` dan diubah ke huruf besar di setiap itemnya/karakternya menggunakan `.toUpperCase()`.