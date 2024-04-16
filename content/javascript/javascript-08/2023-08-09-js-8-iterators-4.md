+++
title = "Javascript 08: filter"
draft = false
weight = 4
tags = ['javascript']
+++

Sama seperti `.map()`, `.filter()` juga menghasilkan array baru tapi sesudah *menyaring* beberapa item dari array yang aslinya.

Mem*filter* angka yang yang lebih kecil dari 1150

```js
const accumulatedPoints = [1123,1131,1242,1452,1834,1551,1928,1102,1009];

const filteredPoints = accumulatedPoints.filter(function (pts){
    return pts < 1150;
});

console.log(filteredPoints);
```
```plain
[ 1123, 1131, 1102, 1009 ]
```
