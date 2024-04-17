+++
title = "Rest Parameter"
draft = false
weight = 3
tags = ['javascript']
+++

Mirip dengan **Spread Operator** secara sintaks dan sifat, namun Rest Parameter bukanlah Spread Operator.

Rest Parameter hanya ada dalam parameter fungsi dengan aturan:

- Hanya boleh diletakkan sebanyak sekali dalam sebuah fungsi.
- Hanya boleh diletakkan di paling ujung/akhir parameter fungsi jika ada parameter lain.

```js
function func(...rest) {
  return rest
}

console.log(func(2, 4, 6)) // [2, 4, 6]
```
Hasil *return* `rest` berbentuk array.


Menjumlahkan semua yang ada di argument.

```js
function func(...rest) {
  return rest.reduce((a, b) => a + b)
}

console.log(func(2, 4, 6)); // 12
```

Menjumlahkan semua yang ada di parameter `rest` dikali `multiplier`.

```js
function func(multiplier, ...rest) {
  return rest.map(x => multiplier * x).reduce((x, y) => x + y)
}

console.log(func(10, 2, 4, 6)); //120
```