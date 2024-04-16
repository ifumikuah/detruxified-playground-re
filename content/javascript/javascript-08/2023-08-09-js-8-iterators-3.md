+++
title = "Javascript 08: map"
draft = false
weight = 3
tags = ['javascript']
+++

`.map()` memanipulasi semua item di sebuah array dan menyimpannya di array baru.

Array baru ini disimpan di sebuah variable.

```js
const numArray = [1,2,3,4,5,6,7,8,9];

const mapNumber = numArray.map(function (xTen){
    return xTen * 10;
});

console.log(mapNumber);
```
```plain
[10, 20, 30, 40, 50, 60, 70, 80, 90]
```

### Mengambil huruf pertama dari string array

```js
const terms = ["Portable", "Operating", "System", "Interface", "X"];

const abbr = terms.map(function(x){
    return x[0];
});

console.log(abbr.join(""));
```
```plain
POSIX
```
