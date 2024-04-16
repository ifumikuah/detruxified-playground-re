+++
title = "Javascript 01: Operator Aritmatik"
draft = false
weight = 4
tags = ['javascript']
+++


### Sinopsis

```js
console.log(3 + 4);
console.log(5 - 1);
console.log(4 * 2);
console.log(9 / 3);
```

### Details

Empat operator matematika dasar bertugas untuk memproses dua atau lebih angka sesuai dengan operator yang diberikan.

```js
console.log(5*5);
```
Output
```cmd
25
```

### modulo

Operator terakhir adalah modulus atau *modulo*, menghasilkan sisa dari pembagian.

Misal, 15 dibagi 4 adalah 3 dan bersisa 3 (3 * 4 = 12) maka *modulo* nya adalah 3 (15 - 12)
```js
console.log(15 % 4);
```
Output
```cmd
3
```

Jika pembagian tidak ada sisanya (pembagian pada umumnya), maka *modulo* nya adalah `0`
```js
console.log(12 % 2);
```
Output
```cmd
0
```