+++
title = "Nullish coalescing operator"
draft = false
weight = 9
tags = ['javascript']
+++

OR `||` operator akan return nilai kanan atau kiri jika salah satunya truthy, namun batasan dari operator ini adalah ketika operator tersebut menemukan value yang seharusnya di evaluasi sebagai true as intended seperti `0`, `false` atau `""`.
 
```js
function findNum(arr, num) {
	return arr.find(x => x === num) || -1;
}
```

Fungsi diatas return angka `num` yang dicari dalam array jika ditemukan, atau `-1` jika tidak ditemukan.

`Array.protytype.find()` return `undefined` jika element tidak ditemukan. Bagaimana jika user ingin mencari angka 0 yang notabenenya falsy ?

```js
const search = findNum([1, 2, 4, 0, 5], 0);
console.log(search) // -1
```

## ?? Operator

Nullish coalescing `??` operator akan return nilai kanan jika sisi kiri bernilai `null` atau `undefined`

```js
function findNum(arr, num) {
	return arr.find(x => x === num) ?? -1;
}
```

```js
const search = findNum([1, 2, 4, 0, 5], 0);
console.log(search) // 0
```

### Limitasi

Walaupun terlihat seperti logical operator, `??` tidak bisa digabungkan dengan operator lain seperti `&&` atau `||` secara langsung.

Salah satunya cara adalah dengan membuat parenthesis di logika tersebut.

```js
const logic = (null ?? false) || "baz";
console.log(logic) // "baz"
```