+++
title = "Javascript 03 Project: Magic 8 Ball"
draft = false
weight = 10
tags = ['javascript', 'coding project']
+++

# Details

Membuat permainan [Magic 8 Ball](https://en.wikipedia.org/wiki/Magic_8_Ball) menggunakan switch case di Javascript.

# Briefing

User menginput sebuah pertanyaan, lalu 8 Ball akan menjawab pertanyaan berdasarkan angka random.

# Steps

```js
let userName "";

userName ? console.log(`Welcome!, ${userName}`)
: console.log("Welcome!");
```
Ucapan Selamat Datang, bagian pertama akan mencetak selamat datang untuk `userName`, jika kosong maka hanya ada ucapan Selamat Datang.

```js
const dialogUsername = userName || "Stranger";
const userQuestion = "How are you ?";

console.log(`${dialogUsername} : ${userQuestion}`);
```
Pertanyaan, membuat dialog pertanyaan untuk User, jika nama user tidak ada maka `Stranger` akan memulai dialog.

```js
const randomNumber = Math.floor(Math.random() * 8);
```
Random number, terdapat 8 jawaban acak dari 8 Ball, ini akan meng-output angka 0 - 7 dengan cara :
- `Math.random()` akan *generate* angka 0.{1-9}, misal. 0.3
- Lalu dikalikan dengan `8`, misal. 0.3 * 8 = 2.4
- `Math.floor()` akan membulatkan angka tersebut, misal 2

```js
let eightBall = "";
```
`eightBall`, mempersiapkan variabel `eightBall` untuk jawaban.

```js
switch (randomNumber) {
    case 7 :
        eightBall = "It is certain";
        break;
    case 6 :
        eightBall = "It is decidedly so";
        break;
    case 5 :
        eightBall = "Reply hazy try again";
        break;
    case 4 :
        eightBall = "Cannot predict now";
        break;
    case 3 :
        eightBall = "Do not count on it";
        break;
    case 2 :
        eightBall = "My sources say no";
        break;
    case 1 :
        eightBall = "Outlook not so good";
        break;
    case 0 :
        eightBall = "Signs point to yes";
        break;
}
```
Pilihan, terdapat 8 jawaban berdasarkan hasil dari `randomNumber`.

```js
console.log(eightBall);
```
Mencetak jawaban dari `eightBall`

# Full Code

```js
let userName = "";

userName ? console.log(`Welcome!, ${userName}`)
: console.log(`Welcome!`);

const dialogUserName = userName || "Stranger"
const userQuestion =  "How are you ?";
console.log(`${dialogUserName} : ${userQuestion}`);

const randomNumber = Math.floor(Math.random() * 8);

let eightBall = "";

switch (randomNumber) {
    case 7 :
        eightBall = "It is certain";
        break;
    case 6 :
        eightBall = "It is decidedly so";
        break;
    case 5 :
        eightBall = "Reply hazy try again";
        break;
    case 4 :
        eightBall = "Cannot predict now";
        break;
    case 3 :
        eightBall = "Do not count on it";
        break;
    case 2 :
        eightBall = "My sources say no";
        break;
    case 1 :
        eightBall = "Outlook not so good";
        break;
    case 0 :
        eightBall = "Signs point to yes";
        break;
}

console.log(eightBall); 
```