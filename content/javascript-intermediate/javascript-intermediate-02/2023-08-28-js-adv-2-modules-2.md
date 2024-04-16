+++
title = "Javascript Intermediate 02: Node Environment"
draft = false
weight = 2
tags = ['javascript']
+++

Modules adalah file yang terpisah dari file utama kode javascript. File yang terpisah ini pada umumnya adalah fungsi untuk memproses data yang ada di file utama.

```plain
    
    |
    |- areaCalculator/
        |
        |- circle.js -> berisi fungsi untuk kalkukasi lingkaran
        |
        |- square.js -> berisi fungsi untuk kalkukasi persegi
        |
        |- calculator.js -> ini adalah file utama.
```
Diatas adalah contoh sederhana untuk membuat program kalkulator dengan 2 fungsi utama, yaitu kalkulasi luas lingkaran dan persegi. `calculator.js` akan dieksekusi dengan lingkungan node.

## Prerequisites

Pastikan kamu sudah menginstall [node.js](https://nodejs.org/en/download/current).

## Codes

Berikut adalah code `circle.js`
```js
const circleArea = (radius) => Math.PI * radius * radius;

module.exports.circleArea = circleArea;
```
`square.js`
```js
module.exports.squareArea = (side) => side * side;
```
Terakhir, adalah program utama `calculator.js`
```js
const circle = require('./circle');
const square = require('./square.js');

const calcCircle = circle.circleArea;
const calcSquare = square.squareArea;

const numberInput = process.argv[2];
const shapeToCalc = process.argv[3];

if (shapeToCalc === 'circle') {
    const output = calcCircle(numberInput);
    process.stdout.write(`${output}`);
} else if (shapeToCalc === 'square') {
    const output = calcSquare(numberInput);
    process.stdout.write(`${output}`);
} else {
    process.stdout.write("Please insert `square` or `circle`!");
}
```

## Keys

### module.exports
Meng-export sebuah fungsi atau variable kemana saja.

```js
module.exports.squareArea = (side) => side * side;
```

Export fungsi `squareArea()`, jika digunakan oleh file lain misal. `calculator.js`, maka siap panggil dengan key `requireVar.squareArea()`

### require()
Digunakan untuk mereferensikan module yang di import.

```js
const requireVar = require('./square.js');
```

Akan import semua yang ada di `square.js` dan siap dipakai. Di kasus ini, gunakan `requireVar.squareArea()` untuk memanggilnya.

### process.argv[]

`process.argv[]` menyimpan urutan parameter di prompt sebagai array di node.

```plain
> node calculator.js 100 circle
### Maka process.argv akan menyimpan array sebagai berikut ###
["node","calculator.js","100","circle"];
```

Menyimpan array index ke 2 sebagai input nomor.
```js
const numberInput = process.argv[2];
```

### process.stdout.write

Mirip seperti `console.log`, Output hasil kalkulasi.