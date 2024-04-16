+++
title = "Javascript 03: Truthy and Falsy"
draft = false
weight = 5
tags = ['javascript']
+++


### Details

Menyatakan sebuah value termasuk *Truthy* atau *Falsy*.

#### Truthy

Dalam tipe data `str`, value yang memiliki isi, apapun isinya contoh: sebuah spasi, akan memiliki nilai Truthy.

Dalam tipe data `number`, value yang memiliki angka selain `0` akan memiliki nilai Truthy

```js
let myVariable = 'I Exist!';
 
if (myVariable) {
   console.log(true)
} else {
   console.log('The variable does not exist.')
}

let myNumber = 1;
 
if (myNumber) {
   console.log(true)
} else {
   console.log('The number does not exist.')
}
```
Output
```plain
true
true
```

#### Falsy

Bernilai `false`, semua value yang merepresentasikan kekosongan akan bernilai `false`, diantaranya :

- `0`
- strings seperti `""` atau `''`
- `null`
- `undefined`
- `NaN`, atau *Not a Number*

```js
let numberOfApples = 0;
 
if (numberOfApples){
   console.log('Let us eat apples!');
} else {
   console.log('No apples left!');
}
```
Output

```plain
No apples left!
```
