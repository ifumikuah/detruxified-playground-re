+++
title = "Javascript 03: Operators"
draft = false
weight = 3
tags = ['javascript']
+++

### Sinopsis

```js
if (10 <= 7)
```

### Details

Menggunakan operator dengan statemen if else.

```js
const x = 3
const y = 5
const z = 12

if (x > 4) {
    console.log("benar, 3 lebih besar dari 4");
} else {
    console.log("salah, 3 lebih kecil dari 4");
}

if (y === 5) {
    console.log("benar, 5 sama dengan 5");
} else {
    console.log("salah, 5 bukanlah 5");
}

if (z >= 12) {
    console.log("benar, 12 sama dengan atau lebih besar dari 12");
} else {
    console.log("salah, 12 tidak sama dengan atau lebih besar dari 12");
}
```

Output

```plain
salah, 3 lebih kecil dari 4
benar, 5 sama dengan 5
benar, 12 sama dengan lebih besar dari 12
```

Operator yang bisa digunakan : `>`,`<`,`<=`,`>=`,`===`,`!==`

`!==` adalah kebalikan dari `===`

```js
const x = 10;

if (x !== 5) {
    console.log("benar, 10 bukanlah 5");
} else {
    console.log("salah, 10 adalah 5");
}
```

Output

```plain
benar, 10 bukanlah 5
```