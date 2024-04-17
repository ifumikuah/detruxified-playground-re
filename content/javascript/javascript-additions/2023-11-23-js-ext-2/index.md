+++
title = "Spread Operator"
draft = false
weight = 2
tags = ['javascript']
+++

Spread operator `[...]` digunakan sebagai "ekspansi" iterable seperti array, string dan object.

```js
const nA = [1, 2, 3]
const nB = [4, 5]
const nC = [...nA, ...nB]

console.log(nC) // [ 1, 2, 3, 4, 5 ]

const nD = [1, ...nB, 6]
console.log(nD) // [ 1, 4, 5, 6 ]
```

## Spread operator untuk object literal

Mengubah array menjadi object, sintaks ini membuat index array menjadi key dan value menjadi value object.

```js
const animals = ["Cow", "Chicken", "Goose", "Pigeon", "Dog"]
console.log({...animals}); // { 0: 'Cow', 1: 'Chicken', 2: 'Goose', 3: 'Pigeon', 4: 'Dog' }
```

Menggabungkan dua object

```js
const robot = {
  "name": "Omega",
  "weapon": "Laser"
}
const limbs = {
  "arms": "Carbon nanotube",
  "legs": "Infused ceramics"
}

console.log({...robot, ...limbs})
/*{ 
  name: 'Omega',
  weapon: 'Laser',
  arms: 'Carbon nanotube',
  legs: 'Infused ceramics' 
}*/
```

## Function call

Menggunakan spread operator didalam parameter fungsi

```js
const nums = [4, 5, 6]
function addition(x, y, z) {
  return x + y + z
}

console.log(addition(...nums)); //15
```